<script>
export default {
  name: "instock",
  data() {
    return {
      value: 0,
      warehouseList: [
        {value: 0, text: "篮球"},
        {value: 1, text: "足球"},
        {value: 2, text: "游泳"},
      ],
    };
  },
  methods: {
    change(e) {
      console.log("e:", e);
    },
    handleQuery() {

    }

  },
}
</script>

<template>
  <view class="container">
    <uni-section title="货物入库目标" type="line" style="padding:0px 15px;">
      <uni-forms ref="queryForm" class="uni-form" label-width="85px">
        <uni-row class="uni-row">
          <!--          <uni-col :span="12">
                      <uni-forms-item label="目标仓库代码" required>
                        &lt;!&ndash;              <uni-easyinput maxlength="60" placeholder="请选择项目园区"/>&ndash;&gt;
                        <uni-data-select :localdata="range">
                        </uni-data-select>
                      </uni-forms-item>
                    </uni-col>-->
          <uni-col :span="24">
            <uni-forms-item label="目标仓库" required>
              <uni-data-select :localdata="warehouseList">
              </uni-data-select>
            </uni-forms-item>
          </uni-col>
          <uni-col :span="24">
            <uni-forms-item label="目标储位" required>
              <uni-data-select :localdata="warehouseList">
              </uni-data-select>
            </uni-forms-item>
          </uni-col>

          <uni-col :span="15">
            <uni-forms-item label="SKU号码" required>
              <uni-easyinput placeholder="请输入仓库"/>
            </uni-forms-item>
          </uni-col>
          <uni-col :span="6" :offset="1">
            <button type="primary" size="mini" @click="handleQuery">模糊检索</button>
          </uni-col>

          <uni-col :span="24">
            <uni-forms-item :labelWidth="80" label="货号">
              <uni-easyinput disabled placeholder="货号"></uni-easyinput>
            </uni-forms-item>
          </uni-col>
          <uni-col :span="24">
            <uni-forms-item :labelWidth="80" label="颜色">
              <uni-easyinput disabled placeholder="颜色"></uni-easyinput>
            </uni-forms-item>
          </uni-col>
          <uni-col :span="24">
            <uni-forms-item :labelWidth="80" label="尺寸">
              <uni-easyinput disabled placeholder="尺寸"></uni-easyinput>
            </uni-forms-item>
          </uni-col>
        </uni-row>

      </uni-forms>
    </uni-section>

    <uni-section title="本次入库情况" type="line" style="padding:0px 15px;">
      <uni-forms ref="baseForm" class="uni-form" label-width="85px">
        <uni-row>
          <uni-col :span="24">
            <uni-forms-item label="单位" required>
              <uni-data-select :localdata="warehouseList">
              </uni-data-select>
            </uni-forms-item>
          </uni-col>

          <uni-col :span="24">
            <uni-forms-item label="入库数量" required>
              <uni-easyinput type="number" placeholder="入库数量"></uni-easyinput>
            </uni-forms-item>
          </uni-col>

        </uni-row>
      </uni-forms>

      <button type="primary" @click="submit('customForm')">确定入库</button>

    </uni-section>

  </view>
</template>

<style scoped lang="scss">

</style>