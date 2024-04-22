<!--拣货（备货）作业-->
<script>
import UniForms from "../../uni_modules/uni-forms/components/uni-forms/uni-forms.vue";
import UniFormsItem from "../../uni_modules/uni-forms/components/uni-forms-item/uni-forms-item.vue";
import UniRow from "../../uni_modules/uni-row/components/uni-row/uni-row.vue";

export default {
  name: "picking-work",
  components: {UniRow, UniFormsItem, UniForms},
  data() {
    return {
      warehouseList: [
        {value: 0, text: "篮球"},
        {value: 1, text: "足球"},
        {value: 2, text: "游泳"},
      ],
      pickingTypeList: [
        {value: 0, text: "客户"},
        {value: 1, text: "货品"},
        {value: 2, text: "销售单号"},
      ],
      pickingStatusList: [
        {value: 0, text: "客户"},
        {value: 1, text: "货品"},
        {value: 2, text: "销售单号"},
      ],
      queryForm: {},
      list: [
        { id: 1,
          orderNumber: 'XXXXXXXXXXXX',
          createTime: '2024/04/01 10:20:00',
          bhtype: '客户',
          ckck: 'G2仓',
          bhstatus: '作业开始'
        },
        {id: 2}, {id: 3},{id: 4}

      ]
    }
  },
  methods: {
    start(id) {
      this.$tab.navigateTo(`/pages/picking/picking-work?id=${id}`)
    }
  }
}
</script>

<template>
  <view class="uni-title uni-common-mt">
    <view class="collapse-container">
    <uni-collapse class="collapse" ref="collapse" >
      <uni-collapse-item title="筛选条件" >
        <view class="content"  >
          <!--        <text class="text">手风琴效果同时只会保留一个组件的打开状态，其余组件会自动关闭。</text>-->
          <uni-forms border label-width="85px">
            <uni-forms-item label="备货单号">
              <uni-easyinput :inputBorder="false" placeholder="请输入备货单号"></uni-easyinput>
            </uni-forms-item>
            <uni-forms-item label="出货仓库">
              <uni-data-select
                  v-model="queryForm.warehouse"
                  :localdata="warehouseList"
                  @click="test"
              ></uni-data-select>
            </uni-forms-item>
            <uni-forms-item label="备货单类型">
              <uni-data-select
                  v-model="queryForm.pickingType"
                  :localdata="pickingTypeList"
              ></uni-data-select>
            </uni-forms-item>
            <uni-forms-item label="备货单状态">
              <uni-data-select
                  v-model="queryForm.pickingStatus"
                  :localdata="pickingStatusList"
              ></uni-data-select>
            </uni-forms-item>
            <uni-forms-item>
              <button class="primary-button" size="mini" type="primary" style="border-radius: 20px;margin-right: 15px">检索</button>
              <button class="primary-button" size="mini" type="primary" style="border-radius: 20px;">重置</button>
            </uni-forms-item>
          </uni-forms>
        </view>
      </uni-collapse-item>
    </uni-collapse>
    </view>

<!--    </view>-->
    <uni-section title="备货清单" type="line" style="padding:0px 15px;">
      <uni-list>
        <uni-list-item class="uni-list-item" v-for="(item, index) in list" :key="index" :title="item.title" :note="item.note" >

          <!-- 内容的简介 -->
          <template v-slot:body>
            <uni-card class="list-card ">
              <uni-row class="uni-row" style="border-bottom: 1px solid rgb(238, 238, 238);margin-bottom: 15px;padding-bottom: 10px;">
                <uni-col :span="12" style="display:flex;">
                  <view class="label label-title">备货单号</view>
                  <view class="label-value">123123</view>
                </uni-col>
                <uni-col :span="12" style="display:flex;justify-content: flex-end">
                  <view class="label label-title">创建时间</view>
                  <view class="label-value">123123</view>
                </uni-col>
              </uni-row>
              <uni-row class="uni-row">
                <uni-col :span="24" style="display:flex;">
                  <view class="label">出货仓</view>
                  <view class="label-value">G2仓库</view>
                </uni-col>

                <uni-col :span="24" style="display:flex;">
                  <view class="label">备货单类型</view>
                  <view class="label-value">客户</view>
                </uni-col>

                <uni-col :span="24" style="display:flex;">
                  <view class="label">备货单状态</view>
                  <view class="label-value" style="color: crimson">作业新建</view>
                </uni-col>
                <uni-col :span="24" style="margin-top:15px;display:flex; border-top: 1px solid rgb(238, 238, 238); padding-top: 15px;">
                  <button class="primary-button" size="mini" type="primary" style="border-radius: 20px;width: 200px;" @click="start(item.id)">开始备货</button>
                </uni-col>
              </uni-row>
            </uni-card>
          </template>
        </uni-list-item>
        <!--        <uni-load-more iconType="circle" status="loding" />-->
      </uni-list>

    </uni-section>
  </view>
  <!--
    <uni-list>
    </uni-list>-->
</template>

<style lang="scss" scoped>
.content {
  padding: 15px;
  height: 400px;
}

.list-card {
  //background-color: #1fbc97a1;
  border-radius: 20px;
  margin: 0px !important;
  padding: 0px !important;;
}

.uni-list-item ::v-deep .uni-card--shadow {
  box-shadow: rgb(66,80,191) 20px 20px 3px 1px !important;
}

.label, .label-value {
  font-size: 13px;
  padding-right: 15px;
  font-weight: bold;
  width: 125px;
  color: #606266;
}
.label-title {
  font-size: 13.5px;
}

.label-value {
  font-weight: bold;
  color: black;
}

.primary-button {
  background-color: rgb(66, 80, 191);
}

.uni-list-item ::v-deep .uni-list-item__container  {
  padding: 0px 0px 0px 0px;
  margin-bottom: 10px;
}

* {
  font-family: "微软雅黑";
}

.bgcor-green {
  background-image: linear-gradient(to bottom, #51e66d, #f7f7f7)
}

.bgcor-yellow {
  background-image: linear-gradient(to bottom, #e0e651, #f7f7f7);
}

.bgcor-red {
  background-image: linear-gradient(to bottom, #e68451, #f7f7f7);
}

// 测试粘性定位
.collapse-container {
  //height: 480px;
  //overflow: auto;
  top:0;
}
.collapse {
  position: sticky;
  top:20px;
}

</style>