<template>
  <div>

    <el-divider />

    <!-- 标题 -->
    <el-row justify="center">
        <h1 class="section-title">Core Contributions</h1>
    </el-row>

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">

            <!-- 折叠列表 -->
            <el-collapse model-value="1" class="collapse" accordion >

                <!-- 第一个折叠列表信息 -->
                <el-collapse-item title="样本的选择影响攻击有效性" name="1">
                    <div>
                        本文发现数据投毒过程中样本的选择策略会极大地影响攻击有效性，选取分类模型进行样本筛选后，选择 logit 值较低的样本进行投毒时能更好地提升攻击效率。
                    </div>
                </el-collapse-item>

                <el-collapse-item title="特征对齐" name="2">
                    <div>
                        本文提出一种新型干净标签攻击框架，它可以通过计算目标标签样本的特征质心，并利用这些质心在源标签样本和目标标签之间建立牢固的关系，从而显著提高攻击成功率。
                    </div>
                </el-collapse-item>

                <el-collapse-item title="全面的实验论证" name="3">
                    <div>
                        本文进行了全面的实证研究，以证明所提出的攻击框架在基准数据集上的有效性，数据集包括 CIFAR-10、CIFAR-100、CelebA 和 Food-10。研究结果一致表明，在严格的限制条件下和现实场景中，
                        本文所提出的方法都取得了较高的攻击成功率，突出了其有效性和鲁棒性。
                    </div>
                </el-collapse-item>

                <!-- <el-collapse-item title="Controllability" name="4">
                    <div>
                        Decision making: giving advices about operations is acceptable, but do
                        not make decisions for the users;
                    </div>
                </el-collapse-item> -->
            </el-collapse>
        </el-col>
    </el-row>

  </div>
</template>
  
<script>
</script>

<style scoped>
.collapse {
    margin-top: 20px;
}
</style>
