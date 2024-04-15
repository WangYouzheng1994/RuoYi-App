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
        {
          orderNumber: 'XXXXXXXXXXXX',
          createTime: '2024/04/01 10:20:00',
          bhtype: '客户',
          ckck: 'G2仓',
          bhstatus: '作业开始'
        },
        {},{}

      ]
    }
  }
}
</script>

<template>
  <view class="uni-title uni-common-mt">
    <uni-collapse accordion>
      <uni-collapse-item title="筛选条件">
        <view class="content">
          <!--        <text class="text">手风琴效果同时只会保留一个组件的打开状态，其余组件会自动关闭。</text>-->
          <uni-forms border label-width="85px">
            <uni-forms-item label="备货单号">
              <uni-easyinput :inputBorder="false" placeholder="请输入备货单号"></uni-easyinput>
            </uni-forms-item>
            <uni-forms-item label="出货仓库">
              <uni-data-select
                  v-model="queryForm.warehouse"
                  :localdata="warehouseList"
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

          </uni-forms>
        </view>
      </uni-collapse-item>
    </uni-collapse>

    <uni-section title="备货清单" type="line" style="padding:0px 15px;">
      <uni-list>
        <uni-list-item v-for="(item, index) in list" :key="index" :title="item.title" :note="item.note">
          <!-- 右侧的图标和文字 -->
<!--          <template v-slot:header>-->
<!--            <view class="uni-list-icon">-->
<!--              <uni-icons type="person" size="20"></uni-icons>-->
<!--              <text>{{ item.author }}</text>-->
<!--            </view>-->
<!--          </template>-->
          <!-- 内容的简介 -->
          <template v-slot:body>
<!--            <view class="uni-list-text">{{ item.orderNumber }}</view>-->
<!--            <uni-forms>
              <uni-forms-item label="姓名">
&lt;!&ndash;                <uni-easyinput placeholder="请输入姓名" />&ndash;&gt;
                <view class="uni-list-text">{{ item.orderNumber }}</view>
              </uni-forms-item>
            </uni-forms>-->
            <uni-card class="list-card" isFull="true">
              <uni-row class="uni-row">
                <uni-col :span="24" style="display:flex;">
                  <view class="label">备货单号</view>
                  <view class="label-value">123123</view>
                </uni-col>
                <uni-col :span="24" style="display:flex;">
                  <view class="label">备货单创建时间</view>
                  <view class="label-value">123123</view>
                </uni-col>

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

                <uni-col :span="24" style="margin-top:15px;display:flex;">
                  <button size="mini" type="primary" >开始备货</button>
                </uni-col>
              </uni-row>
            </uni-card>
<!--
            <uni-card title="基础卡片" :isFull="true" sub-title="副标题" extra="额外信息">
              <text>这是一个通栏卡片 ，通栏没有外边距，左右会贴合父元素。</text>
            </uni-card>-->


            <!--            <view class="item">
                          <view class="label">{{ item.orderNumber }}</view>
                          <view class="label-value">123123</view>
                        </view>
                        <view class="item">
                          <view class="label">{{ item.orderNumber }}</view>
                          <view class="label-value">123123</view>
                        </view>-->
<!--            <view><button>asdf</button></view>-->
          </template>
          <!-- 额外的图标 -->
<!--          <template v-slot:footer>-->
<!--            <view class="uni-list-icon">-->
<!--              <button>确认备货</button>-->
<!--            </view>-->
<!--          </template>-->
        </uni-list-item>
<!--        <uni-load-more iconType="circle" status="loding" />-->
      </uni-list>

    </uni-section>
  </view>
  <!--
    <uni-list>
    </uni-list>-->
</template>

<style lang="scss">
.content {
  padding: 15px;
  height: 300px;
}

.list-card {
  background-color: #95F204
}

.label,.label-value {
  font-size: 13px;
  padding-right: 15px;
  font-weight: bold;
  width: 125px;
  color: #606266;
}
.label-value {
  font-weight: bold;
  color: black;
}


</style>