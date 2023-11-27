<template>
    
    <div>
        <el-menu router style="border: none;" :default-active="$route.path">
          <!-- index路径对应router中的path -->
          <!-- default-active使el-menu-item标签中对应index 的高亮  -->
          <el-menu-item index="/">
            <template slot="title">
              <i class="el-icon-house"></i>
              <span>系统首页</span>
            </template>
          </el-menu-item>
          <el-menu-item index="/element">Element</el-menu-item>
          
          <el-submenu>
            <template slot="title">
              <i class="el-icon-menu"></i>
              <span>信息管理</span>
            </template>
            <el-menu-item>用户信息</el-menu-item>
          </el-submenu>
        </el-menu>
        <!-- <el-row>
            <el-col :span="6">
                <div style="height: 300px; width: 100%; background-color: skyblue;"></div>
            </el-col>
            <el-col :span="6">
                <div style="height: 300px; width: 100%; background-color: pink;"></div>
            </el-col>
        </el-row> -->

        <el-row>
            <el-col :span="6">
                <div style="padding: 10px;border: 1px solid #ccc; text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="color: red;">价格：¥99.00</div>
                </div>
            </el-col>
            <el-col :span="6">
                <div style="padding: 10px;border: 1px solid #ccc; text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="color: red;">价格：¥99.00</div>
                </div>
            </el-col>
            <el-col :span="6">
                <div style="padding: 10px;border: 1px solid #ccc; text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="color: red;">价格：¥99.00</div>
                </div>
            </el-col>
            <el-col :span="6">
                <div style="padding: 10px;border: 1px solid #ccc; text-align: center;">
                    <img style="width: 80%;" src="@/assets/logo.png" alt="">
                    <div style="color: red;">价格：¥99.00</div>
                </div>
            </el-col>
        </el-row>

        <el-row>
            <el-col :span="24">
                <el-button type="primary">主要的按钮</el-button>
                <el-button type="danger">危险的按钮</el-button>
                <el-button type="warning">警告的按钮</el-button>
                <el-button type="info">提示的按钮</el-button>
                <el-button type="success">成功的按钮</el-button>
                <el-button>默认的按钮</el-button>

                <el-button type="primary" plain>朴素的主要按钮</el-button>


                <el-button circle icon="el-icon-edit" type="primary"/>
                <el-button circle icon="el-icon-delete" type="danger"/>
            </el-col>
        </el-row>

        <el-row style="margin-top: 20px;">
            <el-col>
                <el-input style="width: 200px;" v-model="value" placeholder="请输入内容"></el-input>
                <el-input type="textarea" style="width: 200px;" v-model="value1"></el-input>
                <el-input show-password style="width: 200px;" v-model="password" placeholder="请输入密码"></el-input>
                <!-- prefix-icon 在前面添加图标 -->
                <el-input style="width: 200px;" v-model="value2" prefix-icon="el-icon-search" placeholder="请输入内容"></el-input>
                <!-- suffix-icon 在后面添加图标 -->
                <el-input style="width: 200px;" v-model="value2" suffix-icon="el-icon-user" placeholder="请输入内容"></el-input>
                <!-- clearable一键删除 -->
                <el-input style="width: 200px;" clearable v-model="value" placeholder="请输入内容"></el-input> 
            </el-col>

        </el-row>

        <el-row style="margin: 20px 0;">
            <el-autocomplete v-model="keyword" style="width: 300px;" placeholder="请输入内容，我来猜一猜" :fetch-suggestions="querySearch" :trigger-on-focus="false">

            </el-autocomplete>

        </el-row>

        <el-row>
            <el-select v-model="select" @change="changeSelect">
                <el-option v-for="item in fruits" :key="item.id" :label="item.name" :value="item.name"></el-option>
            </el-select>
        </el-row>
        <!-- 通过选择姓名返回card -->
        <el-row>
            <el-select v-model="select" @change="changeSelectUser">
                <el-option v-for="item in users" :key="item.card" :label="item.name" :value="item.card"></el-option>
            </el-select>
            <!-- 可通过label搜索 -->
            <el-select v-model="select" @change="changeSelectUser" filterable>
                <el-option v-for="item in users2" :key="item.card" :label="item.label" :value="item.card"></el-option>
            </el-select>
        </el-row>
        <el-row>
            <!-- 通过value-format格式传值 -->
            <el-date-picker v-model="date" type="date" placeholder="请选择日期" value-format="yyyy-MM-dd"></el-date-picker>
            <el-date-picker v-model="datetime" type="datetime" placeholder="请选择日期时间" value-format="yyyy-MM-dd HH:mm:ss" @change="changeTime"></el-date-picker>
            <el-date-picker v-model="daterange" type="daterange" start-placeholder="请选择开始时间" end-placeholder="请选择结束时间" value-format="yyyy-MM-dd" @change="changeDateRange"></el-date-picker>
        </el-row>
        <el-row style="margin: 20px 0;">
            <el-table :data="tableData" border>
                <el-table-column label="序号" prop="id" align="center"></el-table-column>
                <el-table-column label="姓名" prop="name" align="center"></el-table-column>
                <el-table-column label="地址" prop="address" align="center"></el-table-column>
                <el-table-column label="年龄" prop="age" align="center"></el-table-column>
                <el-table-column label="操作">
                    <template v-slot="scope">
                        <el-button type="primary" @click="edit(scope.row)">编辑</el-button>
                    </template>
                </el-table-column>
            </el-table>
        </el-row>
    </div>
</template>

<script>
export default{
    name:"Element",
    data(){
        return{
            tableData : [
                {name:"jokkie",address:"Amoy",age:23,id:1},
                {name:"jokkie2",address:"Amoy",age:23,id:1},
                {name:"jokkie3",address:"Amoy",age:23,id:1},
            ],
            value:'',
            value1:'',
            password:'',
            value2:'',
            keyword:'',
            coffee:[{value:"1.星巴克咖啡"},{value:"2.瑞幸咖啡"},{value:"3.库迪咖啡"}],
            select:'',
            fruits:[
                {name:"苹果",id:1},
                {name:"菠萝",id:2},
                {name:"橘子",id:3}
            ],
            users:[
                {name:"Jokkie",card:'2232523414'},
                {name:"Jokkie2",card:'34541343254'},
                {name:"Jokkie3",card:'12315452341231'}
            ],
            users2:[
                {label:"Jokkie",card:'2232523414'},
                {label:"Jokkie2",card:'34541343254'},
                {label:"Jokkie3",card:'12315452341231'}
            ],
            date:'',
            datetime:'',
            daterange:''
        }
    },
    methods:{
        querySearch(query,cb){
            let res = query ? this.coffee.filter(v => v.value.includes(query)) : this.coffee
            cb(res)
        },
        changeSelect(){
            console.log(this.select);
        },changeSelectUser(){
            console.log(this.select);
        },
        changeTime(){
            console.log(this.datetime);
        },
        changeDateRange(){
            console.log(this.daterange);
        },
        edit(row){
            // alert(row.name)
            // this.$message.success(row.name)
            // this.$notify.success(row.name)

            this.$confirm("这是个弹窗","提示",{
                type:'warning',
            }).then(res =>{
                this.$message.success("点击了确认")
            }).catch(()=>{
                this.$message.success("点击了取消")
            })
        }
    }
}
</script>