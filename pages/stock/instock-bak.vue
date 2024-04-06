<script>
import UniForms from "../../uni_modules/uni-forms/components/uni-forms/uni-forms.vue";
import UniRow from "../../uni_modules/uni-row/components/uni-row/uni-row.vue";
import UniCol from "../../uni_modules/uni-row/components/uni-col/uni-col.vue";

export default {
  name: "instock",
  components: {UniCol, UniRow, UniForms},

  data() {
    return {
      value: 0,
      range: [
        {value: 0, text: "仓库A"},
        {value: 1, text: "仓库B"},
        {value: 2, text: "仓库C"},
      ],
    };
  },
}
</script>

<template>
  <view class="container">
    <uni-section title="检索条件" type="line">
      <uni-forms ref="baseForm" class="uni-form">
        <uni-row class="uni-row">
          <uni-col :span="12">
            <uni-forms-item label="园区" required>
              <!--              <uni-easyinput maxlength="60" placeholder="请选择项目园区"/>-->
              <uni-data-select :localdata="range">
              </uni-data-select>
            </uni-forms-item>
          </uni-col>
          <uni-col :span="12">
            <uni-forms-item label="仓库" required>
              <uni-easyinput placeholder="请输入仓库"/>
            </uni-forms-item>
          </uni-col>
          <uni-col :span="12">
            <uni-forms-item label="库区" required>
              <uni-easyinput placeholder="请输入仓库"/>
            </uni-forms-item>
          </uni-col>

          <uni-col :span="12">
            <uni-forms-item label="库位" required>
              <uni-easyinput placeholder="请输入仓库"/>
            </uni-forms-item>
          </uni-col>

          <uni-col :span="24">
            <uni-forms-item :labelWidth="80" label="计划号" required>
              <uni-easyinput placeholder="请输入仓库"/>
            </uni-forms-item>
          </uni-col>
        </uni-row>

      </uni-forms>
    </uni-section>

    <uni-section title="当前待入库清单" type="line">
      <uni-list>
        <uni-list-item title="列表文字"/>
        <uni-list-item title="列表文字" rightText="右侧文字"/>
        <uni-list-item class="test-uni-list" title="列表文字">
          <template v-slot:body>
            <uni-row class="uni-row">
              <uni-col :span="24">
                <text class="uni-list-item-font">批次号：202205251212401234</text>
              </uni-col>
              <uni-col :span="12">
                <text class="uni-list-item-font">货物编码：pgn001</text>
              </uni-col>
              <uni-col :span="12">
                <text class="uni-list-item-font">货物名称：苹果泥6袋装</text>
              </uni-col>
              <uni-col :span="12">
                <text class="uni-list-item-font">
                  数量： 20
                </text>
              </uni-col>
              <uni-col :span="12">
                  <text class="uni-list-item-font"  style="display: inline-block;vertical-align: middle;">
                    实际数量：
                  </text>
<!--                <input class="uni-input-number" style="width:80px; display: inline-block;vertical-align: middle;" type="number"/>-->
                <uni-easyinput style="width:80px; display: inline-block;vertical-align: middle;"  type="number"></uni-easyinput>
<!--                <uni-number-box :width="20" :value="numberValue" @change="change" />-->
              </uni-col>
            </uni-row>
          </template>
        </uni-list-item>
        <uni-list-chat :avatar-circle="true" title="uni-app"
                       avatar="https://qiniu-web-assets.dcloud.net.cn/unidoc/zh/unicloudlogo.png"
                       note="您收到一条新的消息" time="2020-02-02 20:20"></uni-list-chat>

      </uni-list>

      <!--      <uni-list-chat title="uni-app" note="您收到一条新的消息" time="2020-02-02 20:20" badge-positon="left" badge-text="dot">
              <view class="chat-custom-right">
                <text class="chat-custom-text">刚刚</text>
                &lt;!&ndash; 需要使用 uni-icons 请自行引入 &ndash;&gt;
                <uni-icons type="star-filled" color="#999" size="18"></uni-icons>
              </view>
            </uni-list-chat>-->

    </uni-section>

    <button type="primary" loading="true">页面主操作 Loading</button>
  </view>
</template>

<style scoped lang="scss">
.form-item {
  display: flex;
  align-items: center;
}

.uni-form {
  margin-left: 10px;
  margin-right: 10px;
}

//.uni-col {
//  padding-right: 10px !important;
//}
/deep/ .uni-forms-item__label {
  padding-left: 10px;
}

.uni-list-item-font {
  font-size: 12px;
}
.uni-row {
  width: 100%;
}
uni-view.test-uni-list *.uni-col {
  height: 30px
}
/*uni-view.test-uni-list * uni-view {
  display:flex!important;
  align-items:center;
}*/

</style>