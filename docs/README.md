## sg-radio
sg-radio组件是一个单选框组件

<vuep template="#radio"></vuep>

<script v-pre type="text/x-template" id="radio">
<template>
  <div>
    <el-form ref="form" :model="form" :rules="rules">
      <sg-radio v-model="form.radio1" :options="radioArr1"></sg-radio>
      <sg-radio label="是否产权/户主变更" :label-width="labelWidth" label-position="left" :options="radioArr2" v-model="form.radio2" mark
      @change="change"></sg-radio>
      <sg-radio label="用电性质" :label-width="labelWidth" :options="radioArr3" v-model="form.radio3" prop="radio3" mark="我是提示文字"></sg-radio>
      <el-button @click="submit" type="primary" style="margin-left: 40px;">提交</el-button>
    </el-form>
  </div>
</template>

<script>
 module.exports = {
    data() {
      return {
        labelWidth: '160px',
        radioArr1: [
          {
            key: '1',
            value: '没有label',
            isFlag: false
          },
          {
            key: '2',
            value: '没有label(默认被选中)',
            isFlag: true
          }
        ],
        radioArr2: [
          {
            key: '1',
            value: '不变更（变更服务）',
            isFlag: true,
          },
          {
            key: '2',
            value: '变更（过户服务）',
            isFlag: false
          }
        ],
        radioArr3: [
          {
            key: '1',
            value: '个人',
            isFlag: false
          },
          {
            key: '2',
            value: '企业',
            isFlag: false
          }
        ],
        form: {
          radio1: '2',
          radio2: '1',
          radio3: '',
        },
        rules: {
          radio3: [{required: true, message: '请选择用电性质', trigger: ['blur', 'change']}],
        }
      }
    },
    methods: {
      //提交
      submit(){
        console.log(this.form);
        this.$refs.form.validate((valid, object) => {
          console.log(valid);
          console.log(object);
        });
      },
      change(){
        console.log('change');
      }
    }
  }
</script>



### Attributes

| 参数            | 说明                                                         | 类型                      | 可选值                                                       | 默认值 |
| :-------------- | :----------------------------------------------------------- | :------------------------ | ------------------------------------------------------------ | :----- |
| label           | 标签文本                                                     | string                    | —                                                            | —      |
| label-width     | 表单域标签的的宽度，例如 '50px'。支持 `auto`。               | string                    | —                                                            | —      |
| value / v-model | 绑定值                                                       | string / number / boolean | —                                                            | —      |
| options         | 选项值                                                       | array                     | eg：[{key: '0', value: '个人', isFlag: false}]<br />下方有解释 |        |
| mark            | 是否显示提示说明                                             | string                    | —                                                            | —      |
| required        | 是否必填，如不设置，则会根据校验规则自动生成                 | boolean                   | —                                                            | false  |
| disabled        | 是否禁用                                                     | boolean                   | —                                                            | false  |
| prop            | 表单域 model 字段，在使用 validate、resetFields 方法的情况下，该属性是必填的 | string                    | 传入 Form 组件的 `model` 中的字段                            | —      |
| rules           | 表单验证规则                                                 | object                    | —                                                            | —      |

### Events

| 事件名称 | 说明                   | 回调参数              |
| :------- | :--------------------- | :-------------------- |
| change   | 绑定值变化时触发的事件 | 选中的 Radio label 值 |

## sg-date

<vuep template="#date"></vuep>

<script v-pre type="text/x-template" id="date">
<template>
	<div>
    <el-form ref="form" :model="form" :rules="rules">
      <sg-date start-date="2020-05" end-date="2020-10" format="yyyy/MM" type="month" v-model="form.date1"></sg-date>
      <sg-date label="时间" :label-width="labelWidth" start-date="2020/05" size="mini" format="yyyy/MM" type="month" v-model="form.date2"
      @focus="focus" @blur="blur" @change="change">
      </sg-date>
      <sg-date label="开始时间" :label-width="labelWidth" start-date="2020-11-01" end-date="2020-12-28" size="small" v-model="form.date3" placeholder="请选择开始时间" required></sg-date>
      <sg-date label="结束时间" :label-width="labelWidth" start-date="2020-11-01" end-date="2020-12-28" size="small" mark="我是提示文字" v-model="form.date4" placeholder="请选择结束时间"
      prop="date4"></sg-date>
      <el-button @click="submit" type="primary" style="margin-left: 40px;">提交</el-button>
    <el-form>
  </div>
</template>

<script>
 module.exports = {
    data() {
      return {
        labelWidth: '130px',
        form: {
        	date1: '2020/06',
          date2: '',
          date3: '',
          date4: '',
        },
        rules: {
           date4: [{required: true, message: '请选择结束时间', trigger: 'change'}],
        }
      }
    },
    methods: {
      //提交
      submit(){
        console.log(this.form);
        this.$refs.form.validate((valid, object) => {
          console.log(valid);
          console.log(object);
        });
      },
      change(){
        console.log('change');
      },
      blur(){
        console.log('blur');
      },
      focus(){
        console.log('focus');
      }
    }
  };
</script>

### Attributes

| 参数            | 说明                                                         | 类型                                      | 可选值                                                       | 默认值     |
| :-------------- | :----------------------------------------------------------- | :---------------------------------------- | :----------------------------------------------------------- | :--------- |
| label           | 标签文本                                                     | string                                    | —                                                            | —          |
| label-width     | 表单域标签的的宽度，例如 '50px'。支持 `auto`。               | string                                    | —                                                            | —          |
| value / v-model | 绑定值                                                       | date(DatePicker) / array(DateRangePicker) | —                                                            | —          |
| type            | 显示类型                                                     | string                                    | year/month/date/dates/ week/datetime/datetimerange/ daterange/monthrange | date       |
| startDate       | 开始时间                                                     | sting                                     | —                                                            | —          |
| endDate         | 结束时间                                                     | string                                    | —                                                            | —          |
| format          | 显示在输入框中的格式                                         | string                                    | 见[日期格式](https://element.eleme.cn/#/zh-CN/component/date-picker#ri-qi-ge-shi) | yyyy-MM-dd |
| placeholder     | 非范围选择时的占位内容                                       | string                                    | —                                                            | —          |
| required        | 是否必填，如不设置，则会根据校验规则自动生成                 | boolean                                   | —                                                            | false      |
| disabled        | 是否禁用                                                     | boolean                                   | —                                                            | false      |
| mark            | 是否显示提示说明                                             | string                                    | —                                                            | —          |
| size            | Radio 的尺寸，仅在 border 为真时有效                         | string                                    | medium / small / mini                                        | —          |
| prop            | 表单域 model 字段，在使用 validate、resetFields 方法的情况下，该属性是必填的 | string                                    | 传入 Form 组件的 `model` 中的字段                            | —          |
| rules           | 表单验证规则                                                 | object                                    | —                                                            | —          |
| name            | 原生属性                                                     | string                                    | —                                                            | —          |

### Events

| 事件名称 | 说明                    | 回调参数                                               |
| :------- | :---------------------- | :----------------------------------------------------- |
| change   | 用户确认选定的值时触发  | 组件绑定值。格式与绑定值一致，可受 `value-format` 控制 |
| blur     | 当 input 失去焦点时触发 | 组件实例                                               |
| focus    | 当 input 获得焦点时触发 | 组件实例                                               |


##### sg-select
<vuep template="#SgSelect"></vuep>

<script v-pre type="text/x-template" id="SgSelect">
<template>
<div>
    <el-form :model="elform" ref="elform" :rules="rules">
      <sg-select ref="sgSelect" :optionArr="optionArr" :filterable='true' v-model="elform.region" select-label="daskdjapodjaposjd" prop='region' @selchange='elform.region = $event'></sg-select>
      <sg-select ref="sgSelect" :optionArr="optionArr" v-model="elform.region" prop='region3' @selchange='elform.region3 = $event'></sg-select>
      <sg-select ref="sgSelect2" :optionArr="optionArr" v-model="elform.region2" select-label="大大大" prop='region2' @selchange='elform.region2 = $event'>
        <div slot="select" slot-scope="item">
          {{item}}
          <i style="margin-right:20px;">{{item.data.label}}</i>
        </div> 
      </sg-select>
    </el-form>
    <button @click="text">校验</button>
</div>
</template>

<script>
 module. exports = {

    data() {
      return {
        rules: {
          region2: [{ required: true, message: '请选择活动区域', trigger: 'change' }],
          region: [{ required: true, message: '请选择活动区域fdsfsfd', trigger: 'change' }],
          region3: [{ required: true, message: '请选择活DSSSSSSSSS动区域fdsfsfd', trigger: 'change' }]
        },
        elform: {
          region:'',
          region2:'',
          region3:''
        },
        optionArr: [
        {
          value: "选项1",
          label: "黄金糕",
          isFlag: false
        },
        {
          value: "选项2",
          isFlag: false,
          label: "双皮奶"
        },
        {
          value: "选项3",
          isFlag: false,
          label: "蚵仔煎"
        }
      ]
      }
    },
    methods: {
      text() {
        this.$refs["elform"].validate((valid,object)=> {
          console.log(object);
          if (!valid) {console.log('object');
            this.$nextTick(() => {
              var isError= document.getElementsByClassName("is-error");
              console.log(isError);
              isError[0].querySelector('input').focus();
            })
            return
          }else {console.log(this.elform)}
        })
        // console.log(this.elform)
      }
    }

  }
</script>

###### 属性值

| 参数         | 说明                                                         | 类型    | 默认值 |
| ------------ | ------------------------------------------------------------ | ------- | ------ |
| disabled     | 是否禁用                                                     | boolean | false  |
| placeholder  | 占位符                                                       | string  | 请选择 |
| filterable   | 是否可搜索                                                   | boolean | false  |
| select-label | 是否显示label                                                | string  | —      |
| option-arr   | Option 列表                                                  | array   | —      |
| show-error   | 是否显示校验错误信息(是否必填)                               | boolean | true   |
| prop         | 定义校验的参数                                               | String  | —      |
| label-width  | 表单域标签的宽度，例如 '50px'。作为 Form 直接子元素的 form-item 会继承该值。支持 `auto` 。 | string  | —      |

###### 事件

| 事件名称  | 说明                               | 回调参数     |
| --------- | ---------------------------------- | ------------ |
| selchange | 接受选中的值(选中值发生变化时触发) | 目前的选中值 |

###### Option Attributes

| 参数    | 说明                                      | 类型                 | 默认值 |
| ------- | ----------------------------------------- | -------------------- | ------ |
| value   | 选项的值                                  | string/number/object | —      |
| label   | 选项的标签，若不设置则默认与 `value` 相同 | string/number        | —      |
| key     | 编码值                                    | string/number        | —      |
| is-flag | 是否默认显示                              | Boolean              | false  |

##### sg-upload

<vuep template="#SgUpload"></vuep>

<script v-pre type="text/x-template" id="SgUpload">
<template>
  <div>

    <el-form>
      <sg-upload></sg-upload>
    </el-form>

  </div>
</template>

<script>
 module. exports = {

    data() {
      return {
        
      }
    }

  }
</script>

###### 

###### Attribute

| 参数         | 说明                           | 类型    | 默认值       |
| ------------ | ------------------------------ | ------- | ------------ |
| up-label     | 标签文本的内容                 | string  | —            |
| txtshow      | 是否显示说明文字(最多上传几张) | boolean | true         |
| mb           | 是否显示授权委托书             | boolean | false        |
| mbzt         | 授权委托书(其他)文字           | string  | —            |
| parking-url  | 授权委托书或其他的图片链接地址 | String  | —            |
| updata-txt   | 上传按钮的文字                 | String  | —            |
| quantity     | 上传图片的数量                 | number  | —            |
| empty        | 是否需要清空                   | boolean | true         |
| max-size     | 图片默认大小                   | Number  | 1024         |
| plus         | 上传图片图标                   | String  | el-icon-plus |
| contact-mode | 证件类型                       | string  | 06/13        |
| prop         | 定义校验的参数                 | string  | —            |
| label-width  | label宽度                      | string  | —            |

###### Methods

| 方法名    | 说明         | 参数 |
| --------- | ------------ | ---- |
| send_Data | 传出图片数据 | —    |

## sgUploadId上传身份证
<vuep template="#sgUploadId"></vuep>
<script v-pre type="text/x-template" id="sgUploadId">
<template>
  <div>
    <sg-upload-id :empty='empty' :is-remove='isRemove'></sg-upload-id>
    <button @click="isRemoveFn">上传失败</button>
    <button @click="isEmptyFn">清空</button>
  </div>
</template>
<script>
 module.exports = {
    data() {
      return {
        empty: false, // 是否清空
        isRemove: false, // 上传失败（删除）
      }
    },
    methods: {
      isEmptyFn() {
      this.empty = true
        this.$nextTick(() => {
          this.empty = false
        })
      },
      isRemoveFn(){
        this.isRemove = true
        this.$nextTick(() => {
          this.isRemove = false
        })
      },
    }
  }
</script>




### Attributes

| 参数     | 说明           | 类型    | 可选值 | 默认值                             |
| :------- | :------------- | :------ | :----- | :--------------------------------- |
| empty    | 清空所有       | Boolean | —      | false                              |
| isRemove | 上传失败       | Boolean | —      | false                              |
| ext      | 限制文件格式   | String  |        | .jpg,.png,.jpeg                    |
| maxSize  | 限制图片最大kb | Number  |        | 1204                               |
| frontImg | 身份证正面图   | base64  |        | data:image/png;base64,iVBORw0KG... |
| backImg  | 身份证背面图   | base64  |        | data:image/png;base64,iVBORw0KG... |

### Events

| 事件名称  | 说明                 | 类型  |
| :-------- | :------------------- | :---- |
| send_Data | 将当前的图片发送出来 | Array |



## sgEquipment下拉表格

<vuep template="#sgEquipment"></vuep>

<script v-pre type="text/x-template" id="sgEquipment">
<template>
  <div>
    <el-form :model="ruleForm" :rules="rules" ref="ruleForm" inline-message>
      <sg-equipment
        :table-data="equipList"
        :ischg-trans="ischgTrans"
        prop="chosen_capacity"
        v-model="ruleForm.chosen_capacity"
        @handle-selection-change='handleSelectionChange'
      >
        <!-- 表格标题 -->
        <template slot="title">
          <p slot="title">当前暂停设备{{ equipList.length }}台， 总容量 {{ total_capacity }}kVA。
              已选择启用设备 {{ chosen_station }}台， 启用设备总容量
              {{ ruleForm.chosen_capacity }}kVA</p>
        </template>

        <!-- 表格内容 -->
        <template slot="tableInfo">
          <el-table-column type="selection" label width="32"></el-table-column>
          <el-table-column prop="tranName" label>
            <template slot-scope="scope">
                <p>
                  <span class="tranClass textOverflow">{{
                    scope.row.tranName
                  }}</span>
                  <span class="tranClass2 textOverflow"
                    >设备编号:{{ scope.row.equipId }}</span
                  >
                  <span
                    >设备容量:{{
                      scope.row.plateCap || scope.row.newEquipCap
                    }}&nbsp;kVA</span
                  >
                </p>
              </template>
          </el-table-column>
        </template>
      </sg-equipment>
    
      <h2 @click="handleChgTrans()">
        转换模式
      </h2>
    </el-form>
  </div>
</template>

<script>
 module.exports = {
    data() {
      return {
        rules: {
          chosen_capacity: [
            { required: true, message: '请输入容量', trigger: ['blur', 'change'] },
          ]
        },
        ischgTrans: '1',
        isRemove: false, // 是否删除
        equipList: [
          {
            "equipId": "10000157637",
            "plateCap": "101",
            "tranName": "死数据1",
            "sndsideVoltCode": "AC03802",
            "powersourceNo": "5600774166",
            "frstsideVoltCode": "AC00101",
            "actualStopUseDate": "2016-02-01",
            "runStatusCode": "02",
            "planResumeDate": "2016-07-31"
          },
          {
            "equipId": "10000157637",
            "plateCap": "202",
            "tranName": "死数据2",
            "sndsideVoltCode": "AC03802",
            "powersourceNo": "5600774166",
            "frstsideVoltCode": "AC00101",
            "actualStopUseDate": "2016-02-01",
            "runStatusCode": "02",
            "planResumeDate": "2016-07-31"
          }
        ],
        ruleForm: {
          chosen_capacity: '',
        },
        chosen_station: 0, //  已启动设备台数
        equipListsAct: [], // 选中的设备数据集列表
      }
    },
    computed:{
      // 所有设备总容量
      total_capacity(){
        var num = 0
        this.equipList.forEach(item => {
          num += Number(item.plateCap)
        })
        return num
      }
    },
    watch: {
      'ruleForm.chosen_capacity': {
        handler(newVal, oldVal) {
          console.log(newVal, '父组件newVal')
        }
      }
    },
    methods: {
      handleChgTrans(){
        console.log('转换')
        this.ischgTrans = this.ischgTrans == '1' ? '0' : '1'
        // 重新输入申请恢复容量
        this.ruleForm.chosen_capacity = ''
        // 已启动设备数
        this.chosen_station = 0;
      },
      // 选中的设备
      handleSelectionChange(val) {
        console.log(val,'选中的设备')
        // 重新设置为空
        this.ruleForm.chosen_capacity = ''; // 已启用设备总容量
        this.chosen_station = val.length; // 已启动设备数

        // 已启用设备总容量
        val.forEach((item, i) => {
          // 加上已勾选的设备容量并转为数字类型
          this.ruleForm.chosen_capacity += parseFloat(item.plateCap || item.newEquipCap);
          // 转化为数字类型
          this.ruleForm.chosen_capacity = parseFloat(this.ruleForm.chosen_capacity)
        });
    
        this.equipListsAct = val
      },
    }
  }
</script>
<style scoped>
/* 文字单行溢出 */
.textOverflow {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  display: inline-block;
  vertical-align: top;
}
/* 设备名称 */
.tranClass {
  width: 200px;
  margin-right: 10px;
}
.tranClass2 {
  width: 230px;
  margin-right: 10px;
}
</style>

### Attributes

| 参数              | 说明                        | 类型    | 可选值 | 默认值        |
| :---------------- | :-------------------------- | :------ | :----- | :------------ |
| tableData         | 表格数据                    | Array   | —      | []            |
| capacity_label    | lable名                     | String  | —      | 申请恢复容量: |
| ischgTrans        | 模式， 1选中设备，2手动输入 | String  |        | 1             |
| isChosen_disabled | 不可更改（只读）            | Boolean |        | false         |

### Events

| 事件名称              | 说明                 | 类型  |
| :-------------------- | :------------------- | :---- |
| handleSelectionChange | 将选中的设备发送出来 | Array |

