<script>
export default {
  name: "instock"
}
</script>

<template>
  <view class="container">
    <uni-section title="入库目标" type="line">
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

  </view>
</template>

<style scoped lang="scss">

</style>