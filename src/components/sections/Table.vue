<script lang="ts" setup>

// 表格数据
const tableData1 = [
{
    method: 'Label-consistent',
    p: '50.0',
    ε: '255/255',
    BA1: '91.5',
    ASR1: '94.5',
    BA2: '92.1',
    ASR2: '1.7',
},
{
    method: 'Hidden Trigger',
    p: '12.5',
    ε: '255/255',
    BA1: '91.3',
    ASR1: '94.8',
    BA2: '91.7',
    ASR2: '4.5',
},
{
    method: 'AdvDoor',
    p: '30.0',
    ε: '16/255',
    BA1: '90.4',
    ASR1: '97.9',
    BA2: '90.7',
    ASR2: '78.2',
},
{
    method: 'Sleeper Agent',
    p: '1.0',
    ε: '16/255',
    BA1: '85.4',
    ASR1: '70.9',
    BA2: '90.5',
    ASR2: '61.3',
},
{
    method: 'Narcissus',
    p: '1.0',
    ε: '16/255',
    BA1: '92.0',
    ASR1: '89.7',
    BA2: '92.3',
    ASR2: '60.8',
},
{
    method: 'Silent Killer',
    p: '1.0',
    ε: '16/255',
    BA1: '83.7',
    ASR1: '86.5',
    BA2: '83.7',
    ASR2: '86.5',
},
{
    method: 'Ours',
    p: '1.0',
    ε: '16/255',
    BA1: '91.7',
    ASR1: '93.1',
    BA2: '91.7',
    ASR2: '93.1',
},
]

const tableData2 = [
{
    method: 'Label-consistent',
    BA: '66.2',
    ASR: '3.7',
    BA1: '75.9',
    ASR1: '5.2',
    BA2: '73.6',
    ASR2: '2.6',
},
{
    method: 'Hidden Trigger',
    BA: '64.3',
    ASR: '6.8',
    BA1: '75.6',
    ASR1: '7.3',
    BA2: '74.5',
    ASR2: '5.0',
},
{
    method: 'AdvDoor',
    BA: '62.7',
    ASR: '74.5',
    BA1: '73.4',
    ASR1: '79.6',
    BA2: '72.9',
    ASR2: '75.1',
},
{
    method: 'Sleeper Agent',
    BA: '61.5',
    ASR: '62.8',
    BA1: '73.8',
    ASR1: '65.5',
    BA2: '71.4',
    ASR2: '60.3',
},
{
    method: 'Narcissus',
    BA: '66.3',
    ASR: '63.4',
    BA1: '75.8',
    ASR1: '66.9',
    BA2: '75.2',
    ASR2: '58.6',
},
{
    method: 'Silent Killer',
    BA: '58.6',
    ASR: '83.7',
    BA1: '70.1',
    ASR1: '88.4',
    BA2: '66.7',
    ASR2: '78.5',
},
{
    method: 'Ours',
    BA: '65.7',
    ASR: '90.1',
    BA1: '76.2',
    ASR1: '94.8',
    BA2: '74.1',
    ASR2: '86.2',
},
]

const tableData3 = [
{
    method: 'Sleeper Agent',
    model: 'ResNet-18',
    v1: 'ResNet-18',

},
{
    method: 'Hidden Trigger',
    BA: '64.3',
    ASR: '6.8',
    BA1: '75.6',
    ASR1: '7.3',
    BA2: '74.5',
    ASR2: '5.0',
},
{
    method: 'AdvDoor',
    BA: '62.7',
    ASR: '74.5',
    BA1: '73.4',
    ASR1: '79.6',
    BA2: '72.9',
    ASR2: '75.1',
},
{
    method: 'Sleeper Agent',
    BA: '61.5',
    ASR: '62.8',
    BA1: '73.8',
    ASR1: '65.5',
    BA2: '71.4',
    ASR2: '60.3',
},
{
    method: 'Narcissus',
    BA: '66.3',
    ASR: '63.4',
    BA1: '75.8',
    ASR1: '66.9',
    BA2: '75.2',
    ASR2: '58.6',
},
{
    method: 'Silent Killer',
    BA: '58.6',
    ASR: '83.7',
    BA1: '70.1',
    ASR1: '88.4',
    BA2: '66.7',
    ASR2: '78.5',
},
{
    method: 'Ours',
    BA: '65.7',
    ASR: '90.1',
    BA1: '76.2',
    ASR1: '94.8',
    BA2: '74.1',
    ASR2: '86.2',
},
]
</script>

<template>
    <div>
        <el-divider />

        <el-row justify="center">
            <h1 class="section-title">Experimental Results</h1>
        </el-row>
        
        <!-- 数据表格 -->
        <el-row justify="center">
            <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">

                <!-- 卡片 -->
                <el-card class="card">

                    <!-- 默认tab -->
                    <el-tabs class="demo-tabs" model-value="Method A">

                    <!-- 第一个tab -->
                    <el-tab-pane label="CIFAR-10 对比实验" name="Method A">

                        <!-- 表格数据 -->
                        <el-table 
                            :data="tableData1"
                            :default-sort="{ prop: '', order: 'descending' }"
                            scrollbar-always-on
                        >
                            <el-table-column prop="method" label="Method" width="140" align="center"/>
                            <el-table-column label="标准设置" align="center">
                                <el-table-column prop="p" label="p (%)" width="60" align="center" sortable/>
                                <el-table-column prop="ε" label="ε" width="90" align="center" sortable/>
                                <el-table-column prop="BA1" label="BA (%)" align="center" width="102" sortable/>
                                <el-table-column prop="ASR1" label="ASR (%)" align="center" width="100" sortable/>
                            </el-table-column>
                            <el-table-column label="严格条件" align="center">
                                <el-table-column prop="BA2" label="BA (%)" align="center" width="100" sortable/>
                                <el-table-column prop="ASR2" label="ASR (%)" align="center" width="98" sortable/>
                            </el-table-column>
                        </el-table>
                    </el-tab-pane>

                    <el-tab-pane label="多个基准数据集上的对比实验" name="Method B">
                        <!-- 表格数据 -->
                        <el-table 
                            :data="tableData2"
                            :default-sort="{ prop: '', order: 'descending' }"
                            scrollbar-always-on
                        >
                            <el-table-column prop="method" label="Method" width="150" align="center"/>
                            <el-table-column label="数据集" align="center">
                                <el-table-column label="CIFAR-100" align="center">
                                    <el-table-column prop="BA" label="BA (%)" width="90" align="center" sortable/>
                                    <el-table-column prop="ASR" label="ASR (%)" width="90" align="center" sortable/>
                                </el-table-column>
                                <el-table-column label="CelebA" align="center">
                                    <el-table-column prop="BA1" label="BA (%)" align="center" width="90" sortable/>
                                    <el-table-column prop="ASR1" label="ASR (%)" align="center" width="90" sortable/>
                                </el-table-column>
                                <el-table-column label="Food-10" align="center">
                                    <el-table-column prop="BA2" label="BA (%)" align="center" width="90" sortable/>
                                    <el-table-column prop="ASR2" label="ASR (%)" align="center" width="90" sortable/>
                                </el-table-column>
                            </el-table-column>
                        </el-table>
                    </el-tab-pane>

                    <el-tab-pane label="黑盒实验" name="Method C">
                        实验指标：ASR (%)
                    </el-tab-pane>

                    <el-tab-pane label="后门防御测试" name="Method D">
                        Method D
                    </el-tab-pane>

                    <el-tab-pane label="消融实验" name="Method E">
                        Method E
                    </el-tab-pane>
                    </el-tabs>

                </el-card>
            </el-col>
        </el-row>

    </div>
</template>

<style scoped>
.card {
    margin-top: 20px;
}
</style>
  