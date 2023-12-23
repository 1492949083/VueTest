<template>
    <div>
        <p>会将表格数据保存到localStorage,使用element-ui</p>
        <table :class="table">
            <thead>
                <tr>
                    <th>id</th>
                    <th>用户名</th>
                    <th>密码</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="item in list" :key="item.id">
                    <td>{{ item.id }}</td>
                    <td>{{ item.username }}</td>
                    <td>{{ item.password }}</td>
                    <td><el-button :class="el_btn" type="danger" size="default" @click="list_del(item.id)">删除</el-button>
                    </td>
                </tr>
                <tr>
                    <td><el-input :class="el_i" type="text" v-model="id" placeholder="请输入id" /></td>
                    <td><el-input :class="el_i" type="text" v-model="username" placeholder="请输入用户名" /></td>
                    <td><el-input :class="el_i" type="text" v-model="password" placeholder="请输入密码" /></td>
                    <td><el-button :class="el_btn" :type=add_btn_type size="default" @click="list_add">添加</el-button>
                    </td>
                </tr>
            </tbody>
        </table>
        <p>{{ msg }}</p>
    </div>
</template>

<style scoped>
.list_table {
    border: 1px solid black;
    width: 60vw;
    border-collapse: collapse;
}

.list_table td,
th {
    height: 4vh;
    border: 1px dashed gray;
    text-align: center;
}

.list_table .el_btn {
    width: 100%;
    height: 100%;
    margin: 0;
}

.list_table .el_i {
    width: 100%;
    height: 100%;
    margin: 0;
}
</style>

<script>
export default {
    data() {
        return {
            table: 'list_table',
            list: [],
            id: '',
            username: '',
            password: '',
            msg: '',
            field: '',
            el_btn: 'el_btn',
            el_i: 'el_i',
            add_btn_type: 'primary',
        }
    },
    methods: {
        list_add() {
            if (this.id != '' && !Number(this.id)){
                alert('id请输入数字');
                return;
            }
            if (this.list_find('id', this.id) != '') {
                alert('id已存在');
                return;
            }
            if (this.list_find('username', this.username) != '') {
                alert('用户名已存在');
                return;
            }
            if (this.username == '' || this.password == '') {
                alert('请填写完整');
                return;
            }

            this.id = Number(this.id)

            //添加数据
            if (this.id == 0) {
                let newId = 0;
                //是否有空位
                let isNull = false;
                for (let i = 0; i < this.list.length; i++) {
                    if (this.list[i + 1] == undefined) break;
                    newId = this.list[i + 1].id;
                    console.log(i);
                    if (this.list[i + 1].id - this.list[i].id > 1) {
                        this.list.push({
                            id: Number(this.list[i].id) + Number(1),
                            username: this.username,
                            password: this.password,
                        });
                        isNull = true;
                        break;
                    }
                }
                console.log(newId);
                if (newId != 0 && !isNull) {
                    if (this.list[0].id != 1) {
                        console.log('newId != 0 && this.list[0] != 1');
                        this.list.push({
                            id: 1,
                            username: this.username,
                            password: this.password,
                        });
                    } else {
                        console.log('newId != 0');
                        this.list.push({
                            id: this.list.length + 1,
                            username: this.username,
                            password: this.password,
                        });
                    }
                }
                if (newId == 0 && this.list.length == 0) {
                    console.log('newId == 0 && this.list.length == 0');
                    this.list.push({
                        id: 1,
                        username: this.username,
                        password: this.password,
                    });
                } else if (newId == 0 && this.list[0].id != 1) {
                    console.log('newId == 0 && this.list[0].id != 1');
                    this.list.push({
                        id: 1,
                        username: this.username,
                        password: this.password,
                    });
                } else if (newId == 0 && this.list.length == 1) {
                    console.log('newId == 0 && this.list.length == 1');
                    this.list.push({
                        id: 2,
                        username: this.username,
                        password: this.password,
                    });
                }
            } else {
                this.list.push({
                    id: this.id,
                    username: this.username,
                    password: this.password,
                });
            }


            this.msg = '添加成功';
            this.id = '';
            this.username = '';
            this.password = '';

            //type change
            this.add_btn_type = 'success';
            setTimeout(() => {
                this.add_btn_type = 'primary';
            }, 1000);
            //以id大小排列数组顺序
            this.list.sort(function (a, b) {
                return a.id - b.id;
            });
        },
        list_del(id) {
            //删除id为id的数据
            this.msg = '删除id为' + id + '的数据成功';
            this.list.splice(this.list.findIndex(item => item.id == id), 1);
        },
        list_select(field) {
            //查找field的数据
            var result = [];
            for (let i = 0; i < this.list.length; i++) {
                result.push(this.list[i][field]);
            }
            console.log(result);
            return result;
        },
        list_find(field, value) {
            //查找field为value的数据
            var result = [];
            for (let i = 0; i < this.list.length; i++) {
                if (this.list[i][field] == value) {
                    result.push(this.list[i]);
                }
            }
            console.log(result);
            return result;
        },

    },
    //如果list改变，就保存到localStorage
    watch: {
        list: {
            handler: function (val) {
                localStorage.setItem('list', JSON.stringify(val));
            },
            deep: true
        }
    },
    //如果list为空，就从localStorage读取
    created() {
        if (localStorage.getItem('list') != null) {
            this.list = JSON.parse(localStorage.getItem('list'));
        }
    }
}
</script>