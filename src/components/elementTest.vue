<template>
  <el-container style="height: 600px; border: 1px solid #eee">
    <el-aside width="200px" style="background-color: rgb(238, 241, 246)">
      <el-menu :default-openeds="['1', '3']">
        <el-submenu index="1">
          <template slot="title"><i class="el-icon-message"></i>导航一</template>
          <el-menu-item-group>
            <template slot="title">分组一</template>
            <el-menu-item index="1-1">选项1</el-menu-item>
            <el-menu-item index="1-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="1-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="1-4">
            <template slot="title">选项4</template>
            <el-menu-item index="1-4-1">选项4-1</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title"><i class="el-icon-menu"></i>导航二</template>
          <el-menu-item-group>
            <template slot="title">分组一</template>
            <el-menu-item index="2-1">选项1</el-menu-item>
            <el-menu-item index="2-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="2-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="2-4">
            <template slot="title">选项4</template>
            <el-menu-item index="2-4-1">选项4-1</el-menu-item>
          </el-submenu>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title"><i class="el-icon-setting"></i>导航三</template>
          <el-menu-item-group>
            <template slot="title">分组一</template>
            <el-menu-item index="3-1">选项1</el-menu-item>
            <el-menu-item index="3-2">选项2</el-menu-item>
          </el-menu-item-group>
          <el-menu-item-group title="分组2">
            <el-menu-item index="3-3">选项3</el-menu-item>
          </el-menu-item-group>
          <el-submenu index="3-4">
            <template slot="title">选项4</template>
            <el-menu-item index="3-4-1">选项4-1</el-menu-item>
          </el-submenu>
        </el-submenu>
      </el-menu>
    </el-aside>

    <el-container>
      <el-header style="text-align: right; font-size: 12px">

        <el-dropdown>
          <i class="el-icon-setting" style="margin-right: 15px"></i>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>查看</el-dropdown-item>
            <el-dropdown-item>新增</el-dropdown-item>
            <el-dropdown-item>删除</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <span>王小虎</span>


      </el-header>

      <el-main>
        <div>
          <el-alert title="带辅助性文字介绍" type="success" description="这是一句绕口令：黑灰化肥会挥发发灰黑化肥挥发；灰黑化肥会挥发发黑灰化肥发挥。 黑灰化肥会挥发发灰黑化肥黑灰挥发化为灰……">
          </el-alert>
          <el-alert title="成功提示的文案" type="success" description="文字说明文字说明文字说明文字说明文字说明文字说明" show-icon>
          </el-alert>
          <el-alert title="消息提示的文案" type="info" center show-icon>
          </el-alert>
          <el-alert title="警告提示的文案" type="warning" show-icon>
          </el-alert>
          <el-alert title="设置了回调的 alert" type="warning" @close="hello">
          </el-alert>
        </div>

        <div>
          <el-dialog title="外层 Dialog" :visible.sync="outerVisible">
            <el-dialog width="30%" title="内层 Dialog" :visible.sync="innerVisible" append-to-body>
            </el-dialog>
            <div slot="footer" class="dialog-footer">
              <el-button @click="outerVisible = false">取 消</el-button>
              <el-button type="primary" @click="innerVisible = true">打开内层 Dialog</el-button>
            </div>
          </el-dialog>

          <el-dialog title="提示" :visible.sync="centerDialogVisible" width="30%" center>
            <span>需要注意的是内容是默认不居中的</span>
            <span slot="footer" class="dialog-footer">
              <el-button @click="centerDialogVisible = false">取 消</el-button>
              <el-button type="primary" @click="centerDialogVisible = false">确 定</el-button>
            </span>
          </el-dialog>


        </div>

        <!-- 注：
         1. border：显示单元格边框线；
         2. stripe：斑马线，隔行同色；
         3. 只要在el-table元素中定义了height属性，即可实现固定表头的表格；
         4. 固定列需要使用fixed属性，它接受 Boolean 值或者leftright，表示左边固定还是右边固定。
         5. 实现多选非常简单: 手动添加一个el-table-column，设type属性为selection即可；默认情况下若内容过多会折行显示，若需要单行显示可以使用show-overflow-tooltip属性，它接受一个Boolean，为true时多余的内容会在 hover 时以 tooltip 的形式显示出来。
         6. Element 提供了两种调用 Loading 的方法：指令和服务。对于自定义指令v-loading，只需要绑定Boolean即可。默认状况下，Loading 遮罩会插入到绑定元素的子节点，通过添加body修饰符，可以使遮罩插入至 DOM 中的 body 上。
         7. 在绑定了v-loading指令的元素上添加element-loading-text属性，其值会被渲染为加载文案，并显示在加载图标的下方。类似地，element-loading-spinner和element-loading-background属性分别用来设定图标类名和背景色值。-->
        <div>
          <el-table :data="tableData" stripe height="300" @selection-change="handleSelectionChange" tooltip-effect="dark"
            ref="multipleTable" v-loading="loading" element-loading-text="拼命加载中" element-loading-spinner="el-icon-loading"
            element-loading-background="rgba(0, 0, 0, 0.8)">
            <el-table-column type="selection" width="55">
            </el-table-column>
            <el-table-column fixed prop="date" label="日期" width="180" @click.left="mouseLeft" @click.right="mouseRight">
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="180"> </el-table-column>
            <el-table-column prop="province" label="省份" width="180"> </el-table-column>
            <el-table-column prop="city" label="市区" width="180"> </el-table-column>
            <el-table-column prop="address" label="地址" width="350"> </el-table-column>
            <el-table-column prop="zip" label="邮编" width="180"> </el-table-column>
            <el-table-column fixed="right" label="操作" width="200">
              <template slot-scope="scope">
                <el-button @click="handleClick1(scope.row)" type="text" size="small">查看</el-button>
                <el-button type="text" size="small">编辑</el-button>
              </template>
            </el-table-column>
          </el-table>
          <div style="margin-top: 20px">
            <el-button @click="toggleSelection([tableData[1], tableData[2]])">切换第二、第三行的选中状态</el-button>
            <el-button @click="toggleSelection()">取消选择</el-button>
            <el-button @click="loadingAction()">显示或关闭loading</el-button>
          </div>
        </div>

        <el-container style="direction:vertical;">

          <div style="width: 100%;background-color: aquamarine;">

            <div class="pad">
              <i class="el-icon-edit"></i>
              <i class="el-icon-share"></i>
              <i class="el-icon-delete"></i>
              <el-button type="primary" icon="el-icon-search">搜索</el-button>

              <el-row>
                <el-button @click="btn(1)">默认按钮</el-button>
                <el-button type="primary" @click="btn(2)">主要按钮</el-button>
                <el-button type="success" @click="btn(3)">成功按钮</el-button>
                <el-button type="info" @click="btn(4)">信息按钮</el-button>
                <el-button type="warning" @click="btn(5)">警告按钮</el-button>
                <el-button type="danger" @click="btn(6)">危险按钮</el-button>
              </el-row>

              <el-row>
                <el-button plain @click="btn(7)">朴素按钮</el-button>
                <el-button type="primary" plain @click="btn(8)">主要按钮</el-button>
                <el-button type="success" plain @click="btn(9)">成功按钮</el-button>
                <el-button type="info" plain @click="btn(10)">信息按钮</el-button>
                <el-button type="warning" plain @click="btn(11)">警告按钮</el-button>
                <el-button type="danger" plain @click="btn(12)">危险按钮</el-button>
              </el-row>

              <el-row>
                <el-button round @click="btn(13)">圆角按钮</el-button>
                <el-button type="primary" round @click="btn(14)">主要按钮</el-button>
                <el-button type="success" round @click="btn(15)">成功按钮</el-button>
                <el-button type="info" round @click="btn(16)">信息按钮</el-button>
                <el-button type="warning" round @click="btn(17)">警告按钮</el-button>
                <el-button type="danger" round @click="btn(18)">危险按钮</el-button>
              </el-row>

              <el-row>
                <el-button icon="el-icon-search" circle @click="btn(19)"></el-button>
                <el-button type="primary" icon="el-icon-edit" circle @click="btn(20)"></el-button>
                <el-button type="success" icon="el-icon-check" circle @click="btn(21)"></el-button>
                <el-button type="info" icon="el-icon-message" circle @click="btn(22)"></el-button>
                <el-button type="warning" icon="el-icon-star-off" circle @click="btn(23)"></el-button>
                <el-button type="danger" icon="el-icon-delete" circle @click="btn(24)"></el-button>
              </el-row>

              <el-row>
                <el-button disabled>默认按钮</el-button>
                <el-button type="primary" disabled>主要按钮</el-button>
                <el-button type="success" disabled>成功按钮</el-button>
                <el-button type="info" disabled>信息按钮</el-button>
                <el-button type="warning" disabled>警告按钮</el-button>
                <el-button type="danger" disabled>危险按钮</el-button>
              </el-row>

              <el-row>
                <el-button plain disabled>朴素按钮</el-button>
                <el-button type="primary" plain disabled>主要按钮</el-button>
                <el-button type="success" plain disabled>成功按钮</el-button>
                <el-button type="info" plain disabled>信息按钮</el-button>
                <el-button type="warning" plain disabled>警告按钮</el-button>
                <el-button type="danger" plain disabled>危险按钮</el-button>
              </el-row>

              <el-button type="text">文字按钮</el-button>
              <el-button type="text" disabled>文字按钮</el-button>

              <el-button type="primary" icon="el-icon-edit"></el-button>
              <el-button type="primary" icon="el-icon-share"></el-button>
              <el-button type="primary" icon="el-icon-delete"></el-button>
              <el-button type="primary" icon="el-icon-search">搜索</el-button>
              <el-button type="primary">上传<i class="el-icon-upload el-icon--right"></i></el-button>

              <el-button-group>
                <el-button type="primary" icon="el-icon-arrow-left">上一页</el-button>
                <el-button type="primary">下一页<i class="el-icon-arrow-right el-icon--right"></i></el-button>
              </el-button-group>
              <el-button-group>
                <el-button type="primary" icon="el-icon-edit"></el-button>
                <el-button type="primary" icon="el-icon-share"></el-button>
                <el-button type="primary" icon="el-icon-delete"></el-button>
              </el-button-group>

              <el-button type="primary" :loading="true">加载中</el-button>

              <el-row>
                <el-button>默认按钮</el-button>
                <el-button size="medium">中等按钮</el-button>
                <el-button size="small" round>小型按钮 圆角</el-button>
                <el-button size="mini" round>超小按钮 圆角</el-button>
              </el-row>
            </div>

            <!-- 标签 -->
            <div class="pad">
              <el-row style="background-color: antiquewhite;">
                <el-link href="https://element.eleme.io" target="_blank">默认链接</el-link>
                <el-link type="primary">主要链接</el-link>
                <el-link type="success" disabled>成功链接 禁用</el-link>
                <el-link type="warning" :underline="false">警告链接 无下划线</el-link>
                <el-link type="danger" disabled>危险链接 禁用</el-link>
                <el-link type="info">信息链接</el-link>
              </el-row>
            </div>

            <!-- 单选 radio -->
            <div class="pad">
              <!-- size：medium / small / mini	 -->
              <div>
                <el-radio-group v-model="radio2" size="medium" @change="cradio">
                  <el-radio-button label="上海"></el-radio-button>
                  <el-radio-button label="北京" disabled></el-radio-button>
                  <el-radio-button label="广州"></el-radio-button>
                  <el-radio-button label="深圳"></el-radio-button>
                </el-radio-group>
              </div>

              <el-radio-group v-model="radio" @change="cradio">
                <el-radio :label="3">备选项</el-radio>
                <el-radio :label="6">备选项</el-radio>
                <el-radio :label="9">备选项</el-radio>
              </el-radio-group>

              <!-- size：medium / small / mini	 -->
              <div style="margin-top: 20px">
                <el-radio v-model="radio2" label="1" border size="medium">备选项1</el-radio>
                <el-radio v-model="radio2" label="2" border size="medium">备选项2</el-radio>
              </div>

              <div style="margin-top: 20px">
                <el-radio-group v-model="radio3" size="small" @change="cradio">
                  <el-radio label="1" border>备选项1</el-radio>
                  <el-radio label="2" border disabled>备选项2</el-radio>
                </el-radio-group>
              </div>
              <div style="margin-top: 20px">
                <el-radio-group v-model="radio4" size="mini" disabled @change="cradio">
                  <el-radio label="1" border>备选项1</el-radio>
                  <el-radio label="2" border>备选项2</el-radio>
                </el-radio-group>
              </div>
            </div>


            <div class="pad" style="background-color: antiquewhite;">
              <div>
                <el-checkbox :indeterminate="isIndeterminate" v-model="checkAll" @change="handleCheckAllChange">全选</el-checkbox>
                <div style="margin: 15px 0;"></div>
                <el-checkbox-group v-model="checkedCities" :min="1" :max="3" @change="handleCheckedCitiesChange">
                  <el-checkbox v-for="city in cities" :label="city" :key="city">{{city}}</el-checkbox>
                </el-checkbox-group>
              </div>

              <!-- size：medium / small / mini	 -->
              <div style="margin-top: 20px">
                <el-checkbox-group v-model="checkboxGroup2" size="medium">
                  <el-checkbox-button v-for="city in cities" :label="city" :key="city">{{city}}</el-checkbox-button>
                </el-checkbox-group>
              </div>
              <div style="margin-top: 20px">
                <el-checkbox-group v-model="checkboxGroup3" size="small">
                  <el-checkbox-button v-for="city in cities" :label="city" :disabled="city === '北京'" :key="city">{{city}}</el-checkbox-button>
                </el-checkbox-group>
              </div>
              <div style="margin-top: 20px">
                <el-checkbox-group v-model="checkboxGroup4" size="mini" disabled>
                  <el-checkbox-button v-for="city in cities" :label="city" :key="city">{{city}}</el-checkbox-button>
                </el-checkbox-group>
              </div>

              <div style="margin-top: 20px">
                <el-checkbox v-model="checked3" label="备选项1" border size="medium"></el-checkbox>
                <el-checkbox v-model="checked4" label="备选项2" border size="small"></el-checkbox>
              </div>
              <div style="margin-top: 20px">
                <el-checkbox-group v-model="checkboxGroup1" size="small">
                  <el-checkbox label="备选项1" border></el-checkbox>
                  <el-checkbox label="备选项2" border disabled></el-checkbox>
                </el-checkbox-group>
              </div>
              <div style="margin-top: 20px">
                <el-checkbox-group v-model="checkboxGroup2" size="mini" disabled>
                  <el-checkbox label="备选项1" border></el-checkbox>
                  <el-checkbox label="备选项2" border></el-checkbox>
                </el-checkbox-group>
              </div>


            </div>

            <div class="box pad">
              <div class="top">
                <el-tooltip class="item" effect="dark" content="Top Left 提示文字" placement="top-start">
                  <el-button>上左</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Top Center 提示文字" placement="top">
                  <el-button>上边</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Top Right 提示文字" placement="top-end">
                  <el-button>上右</el-button>
                </el-tooltip>
              </div>
              <div class="left" style="margin-top: 30px;">
                <el-tooltip class="item" effect="dark" content="Left Top 提示文字" placement="left-start">
                  <el-button>左上</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Left Center 提示文字" placement="left">
                  <el-button>左边</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Left Bottom 提示文字" placement="left-end">
                  <el-button>左下</el-button>
                </el-tooltip>
              </div>

              <div class="right" style="margin-top: 30px;">
                <el-tooltip class="item" effect="dark" content="Right Top 提示文字" placement="right-start">
                  <el-button>右上</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Right Center 提示文字" placement="right">
                  <el-button>右边</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Right Bottom 提示文字" placement="right-end">
                  <el-button>右下</el-button>
                </el-tooltip>
              </div>
              <div class="bottom" style="margin-top: 30px;">
                <el-tooltip class="item" effect="dark" content="Bottom Left 提示文字" placement="bottom-start">
                  <el-button>下左</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Bottom Center 提示文字" placement="bottom">
                  <el-button>下边</el-button>
                </el-tooltip>
                <el-tooltip class="item" effect="dark" content="Bottom Right 提示文字" placement="bottom-end">
                  <el-button>下右</el-button>
                </el-tooltip>
              </div>
            </div>

            <div class="pad" style="background-color: antiquewhite;">
              <el-popover placement="top-start" title="标题" width="200" trigger="hover" content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
                <el-button slot="reference">hover 激活</el-button>
              </el-popover>

              <el-popover placement="bottom" title="标题" width="200" trigger="click" content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
                <el-button slot="reference">click 激活</el-button>
              </el-popover>

              <el-popover ref="popover" placement="right" title="标题" width="200" trigger="focus" content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
              </el-popover>
              <el-button v-popover:popover>focus 激活</el-button>

              <el-popover placement="bottom" title="标题" width="200" trigger="manual" content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。"
                v-model="visible">
                <el-button slot="reference" @click="visible = !visible">手动激活</el-button>
              </el-popover>

              <el-popover placement="top" width="160" v-model="visible2">
                <p>这是一段内容这是一段内容确定删除吗？</p>
                <div style="text-align: right; margin: 0">
                  <el-button size="mini" type="text" @click="visible2 = false">取消</el-button>
                  <el-button type="primary" size="mini" @click="visible2 = false">确定</el-button>
                </div>
                <el-button slot="reference">删除</el-button>
              </el-popover>
            </div>

            <div class="pad">
              <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" @select="handleSelect">
                <el-menu-item index="1">处理中心</el-menu-item>
                <el-submenu index="2">
                  <template slot="title">我的工作台</template>
                  <el-menu-item index="2-1">选项1</el-menu-item>
                  <el-menu-item index="2-2">选项2</el-menu-item>
                  <el-menu-item index="2-3">选项3</el-menu-item>
                  <el-submenu index="2-4">
                    <template slot="title">选项4</template>
                    <el-menu-item index="2-4-1">选项1</el-menu-item>
                    <el-menu-item index="2-4-2">选项2</el-menu-item>
                    <el-menu-item index="2-4-3">选项3</el-menu-item>
                  </el-submenu>
                </el-submenu>
                <el-menu-item index="3" disabled>消息中心</el-menu-item>
                <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
              </el-menu>

              <div class="line"></div>

              <el-menu :default-active="activeIndex2" class="el-menu-demo" mode="horizontal" @select="handleSelect"
                background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
                <el-menu-item index="1">处理中心</el-menu-item>
                <el-submenu index="2">
                  <template slot="title">我的工作台</template>
                  <el-menu-item index="2-1">选项1</el-menu-item>
                  <el-menu-item index="2-2">选项2</el-menu-item>
                  <el-menu-item index="2-3">选项3</el-menu-item>
                  <el-submenu index="2-4">
                    <template slot="title">选项4</template>
                    <el-menu-item index="2-4-1">选项1</el-menu-item>
                    <el-menu-item index="2-4-2">选项2</el-menu-item>
                    <el-menu-item index="2-4-3">选项3</el-menu-item>
                  </el-submenu>
                </el-submenu>
                <el-menu-item index="3" disabled>消息中心</el-menu-item>
                <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">订单管理</a></el-menu-item>
              </el-menu>

              <el-row class="tac">
                <el-col :span="12">
                  <h5>默认颜色</h5>
                  <el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose">
                    <el-submenu index="1">
                      <template slot="title">
                        <i class="el-icon-location"></i>
                        <span>导航一</span>
                      </template>
                      <el-menu-item-group>
                        <template slot="title">分组一</template>
                        <el-menu-item index="1-1">选项1</el-menu-item>
                        <el-menu-item index="1-2">选项2</el-menu-item>
                      </el-menu-item-group>
                      <el-menu-item-group title="分组2">
                        <el-menu-item index="1-3">选项3</el-menu-item>
                      </el-menu-item-group>
                      <el-submenu index="1-4">
                        <template slot="title">选项4</template>
                        <el-menu-item index="1-4-1">选项1</el-menu-item>
                      </el-submenu>
                    </el-submenu>
                    <el-menu-item index="2">
                      <i class="el-icon-menu"></i>
                      <span slot="title">导航二</span>
                    </el-menu-item>
                    <el-menu-item index="3" disabled>
                      <i class="el-icon-document"></i>
                      <span slot="title">导航三</span>
                    </el-menu-item>
                    <el-menu-item index="4">
                      <i class="el-icon-setting"></i>
                      <span slot="title">导航四</span>
                    </el-menu-item>
                  </el-menu>
                </el-col>
                <el-col :span="12">
                  <h5>自定义颜色</h5>
                  <el-menu default-active="2" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
                    background-color="#545c64" text-color="#fff" active-text-color="#ffd04b">
                    <el-submenu index="1">
                      <template slot="title">
                        <i class="el-icon-location"></i>
                        <span>导航一</span>
                      </template>
                      <el-menu-item-group>
                        <template slot="title">分组一</template>
                        <el-menu-item index="1-1">选项1</el-menu-item>
                        <el-menu-item index="1-2">选项2</el-menu-item>
                      </el-menu-item-group>
                      <el-menu-item-group title="分组2">
                        <el-menu-item index="1-3">选项3</el-menu-item>
                      </el-menu-item-group>
                      <el-submenu index="1-4">
                        <template slot="title">选项4</template>
                        <el-menu-item index="1-4-1">选项1</el-menu-item>
                      </el-submenu>
                    </el-submenu>
                    <el-menu-item index="2">
                      <i class="el-icon-menu"></i>
                      <span slot="title">导航二</span>
                    </el-menu-item>
                    <el-menu-item index="3" disabled>
                      <i class="el-icon-document"></i>
                      <span slot="title">导航三</span>
                    </el-menu-item>
                    <el-menu-item index="4">
                      <i class="el-icon-setting"></i>
                      <span slot="title">导航四</span>
                    </el-menu-item>
                  </el-menu>
                </el-col>
              </el-row>


              <el-radio-group v-model="isCollapse" style="margin-bottom: 20px;">
                <el-radio-button :label="false">展开</el-radio-button>
                <el-radio-button :label="true">收起</el-radio-button>
              </el-radio-group>
              <el-menu default-active="1-4-1" class="el-menu-vertical-demo" @open="handleOpen" @close="handleClose"
                :collapse="isCollapse">
                <el-submenu index="1">
                  <template slot="title">
                    <i class="el-icon-location"></i>
                    <span slot="title">导航一</span>
                  </template>
                  <el-menu-item-group>
                    <span slot="title">分组一</span>
                    <el-menu-item index="1-1">选项1</el-menu-item>
                    <el-menu-item index="1-2">选项2</el-menu-item>
                  </el-menu-item-group>
                  <el-menu-item-group title="分组2">
                    <el-menu-item index="1-3">选项3</el-menu-item>
                  </el-menu-item-group>
                  <el-submenu index="1-4">
                    <span slot="title">选项4</span>
                    <el-menu-item index="1-4-1">选项1</el-menu-item>
                  </el-submenu>
                </el-submenu>
                <el-menu-item index="2">
                  <i class="el-icon-menu"></i>
                  <span slot="title">导航二</span>
                </el-menu-item>
                <el-menu-item index="3" disabled>
                  <i class="el-icon-document"></i>
                  <span slot="title">导航三</span>
                </el-menu-item>
                <el-menu-item index="4">
                  <i class="el-icon-setting"></i>
                  <span slot="title">导航四</span>
                </el-menu-item>
              </el-menu>


            </div>


            <div class="pad" style="background-color: antiquewhite;">
              <el-tabs v-model="activeName" @tab-click="handleClick">
                <el-tab-pane label="用户管理" name="first">用户管理</el-tab-pane>
                <el-tab-pane label="配置管理" name="second">配置管理</el-tab-pane>
                <el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
                <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
              </el-tabs>

              <el-tabs v-model="activeName" type="card" @tab-click="handleClick">
                <el-tab-pane label="用户管理" name="first">用户管理</el-tab-pane>
                <el-tab-pane label="配置管理" name="second">配置管理</el-tab-pane>
                <el-tab-pane label="角色管理" name="third">角色管理</el-tab-pane>
                <el-tab-pane label="定时任务补偿" name="fourth">定时任务补偿</el-tab-pane>
              </el-tabs>

              <el-tabs type="border-card">
                <el-tab-pane label="用户管理">用户管理</el-tab-pane>
                <el-tab-pane label="配置管理">配置管理</el-tab-pane>
                <el-tab-pane label="角色管理">角色管理</el-tab-pane>
                <el-tab-pane label="定时任务补偿">定时任务补偿</el-tab-pane>
              </el-tabs>

              <el-radio-group v-model="tabPosition" style="margin-bottom: 30px;">
                <el-radio-button label="top">top</el-radio-button>
                <el-radio-button label="right">right</el-radio-button>
                <el-radio-button label="bottom">bottom</el-radio-button>
                <el-radio-button label="left">left</el-radio-button>
              </el-radio-group>
              <el-tabs :tab-position="tabPosition" style="height: 200px;">
                <el-tab-pane label="用户管理">用户管理</el-tab-pane>
                <el-tab-pane label="配置管理">配置管理</el-tab-pane>
                <el-tab-pane label="角色管理">角色管理</el-tab-pane>
                <el-tab-pane label="定时任务补偿">定时任务补偿</el-tab-pane>
              </el-tabs>


              <el-tabs type="border-card">
                <el-tab-pane>
                  <span slot="label"><i class="el-icon-date"></i> 我的行程</span>
                  我的行程
                </el-tab-pane>
                <el-tab-pane label="消息中心">消息中心</el-tab-pane>
                <el-tab-pane label="角色管理">角色管理</el-tab-pane>
                <el-tab-pane label="定时任务补偿">定时任务补偿</el-tab-pane>
              </el-tabs>


            </div>

            <div class="pad">
              <el-page-header @back="goBack" content="详情页面">
              </el-page-header>
            </div>




          </div>








        </el-container>

      </el-main>
      <el-footer style="text-align: right; font-size: 12px">
        <el-dropdown>
          <i class="el-icon-setting" style="margin-right: 15px"></i>
          <el-dropdown-menu slot="dropdown">
            <el-dropdown-item>查看</el-dropdown-item>
            <el-dropdown-item>新增</el-dropdown-item>
            <el-dropdown-item>删除</el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
        <span>王小虎</span>
      </el-footer>
    </el-container>




  </el-container>


</template>

<style>
  .el-header {
    background-color: #B3C0D1;
    color: #333;
    line-height: 60px;
  }

  .el-footer {
    background-color: #42B983;
    color: #333;
    line-height: 50px;
  }

  .el-aside {
    color: #333;
  }

  .pad {
    padding: 50px 0;
  }

  .box {
    width: 400px;

    .top {
      text-align: center;
    }

    .left {
      float: left;
      width: 60px;
    }

    .right {
      float: right;
      width: 60px;
    }

    .bottom {
      clear: both;
      text-align: center;
    }

    .item {
      margin: 4px;
    }


    .left .el-tooltip__popper,
    .right .el-tooltip__popper {
      padding: 8px 10px;
    }
  }

  .el-menu-vertical-demo:not(.el-menu--collapse) {
    width: 200px;
    min-height: 400px;
  }
</style>

<script>
  const cityOptions = ['上海', '北京', '广州', '深圳'];
  import {
    Loading
  } from 'element-ui';
  export default {
    data() {

      return {
        activeIndex: '1',
        activeIndex2: '1',
        outerVisible: false,
        innerVisible: false,
        centerDialogVisible: false,


        tableData: [],
        multipleSelection: [],
        loading: false,

        radio: 3,
        radio1: '1',
        radio2: '1',
        radio3: '1',
        radio4: '1',
        checked3:'2',
        checked4:'1',

        checkAll: false,
        checkedCities: ['上海', '北京'],
        cities: cityOptions,
        isIndeterminate: true,
        checkboxGroup1: ['上海'],
        checkboxGroup2: ['上海'],
        checkboxGroup3: ['上海'],
        checkboxGroup4: ['上海'],

        visible: false,
        visible2: false,
        isCollapse: true,

        activeName: 'second',
        tabPosition: 'left'
      }
    },
    created() {
      this.tabdata();
    },
    methods: {
      handleSelect(key, keyPath) {
        console.log(key, keyPath);
      },
      tabdata() {
        var ddd = [];
        for (var i = 0; i < 500; i++) {
          const item = {
            date: '2016-05-02',
            name: '王小虎',
            province: '上海',
            city: '普陀区',
            address: '上海市普陀区金沙江路 1518 弄',
            zip: i++
          };
          ddd.push(item);

        }
        this.tableData = ddd;
      },
      mouseLeft(e) {
        alert(JSON.stringify(e));
      },
      mouseRight(e) {
        alert(JSON.stringify(e));
      },
      hello() {
        alert('Hello World!');
      },
      loadingAction() {
        this.loading = !this.loading;
      },
      toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      },
      cradio: function(e) {
        console.log(e);
      },
      handleCheckAllChange(val) {
        this.checkedCities = val ? cityOptions : [];
        this.isIndeterminate = false;
      },
      handleCheckedCitiesChange(value) {
        let checkedCount = value.length;
        this.checkAll = checkedCount === this.cities.length;
        this.isIndeterminate = checkedCount > 0 && checkedCount < this.cities.length;
      },

      btn(e) {
        console.log(e);
        if (e == 0) {
          Loading.service({
            fullscreen: false
          });
        } else if (e == 1) {
          this.$message('这是一条消息提示');
        } else if (e == 2) {
          const h = this.$createElement;
          this.$message({
            message: h('p', null, [
              h('span', null, '内容可以是 '),
              h('i', {
                style: 'color: teal'
              }, 'VNode')
            ])
          });
        } else if (e == 3) {
          //type：success/warning/info/error	
          this.$message({
            message: '恭喜你，这是一条成功消息2',
            type: 'success',
            showClose: true,
            center: true
          });
        } else if (e == 4) {
          this.$message({
            dangerouslyUseHTMLString: true,
            message: '<strong>这是 <i>HTML</i> 片段</strong>'
          });
        } else if (e == 5) {
          this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
            confirmButtonText: '确定',
            cancelButtonText: '取消',
            type: 'warning'
          }).then(() => {
            this.$message({
              type: 'success',
              message: '删除成功!'
            });
          }).catch(() => {
            this.$message({
              type: 'info',
              message: '已取消删除'
            });
          });

        } else if (e == 6) {
          const h = this.$createElement;
          this.$msgbox({
            title: '消息',
            message: h('p', null, [
              h('span', null, '内容可以是 '),
              h('i', {
                style: 'color: teal'
              }, 'VNode')
            ]),
            showCancelButton: true,
            confirmButtonText: '确定',
            cancelButtonText: '取消',
            beforeClose: (action, instance, done) => {
              if (action === 'confirm') {
                instance.confirmButtonLoading = true;
                instance.confirmButtonText = '执行中...';
                setTimeout(() => {
                  done();
                  setTimeout(() => {
                    instance.confirmButtonLoading = false;
                  }, 300);
                }, 3000);
              } else {
                done();
              }
            }
          }).then(action => {
            this.$message({
              type: 'info',
              message: 'action: ' + action
            });
          });
        } else if (e == 7) {
          this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
            confirmButtonText: '确定',
            cancelButtonText: '取消',
            type: 'warning',
            center: true
          }).then(() => {
            this.$message({
              type: 'success',
              message: '删除成功!'
            });
          }).catch(() => {
            this.$message({
              type: 'info',
              message: '已取消删除'
            });
          });
        } else if (e == 8) {
          const h = this.$createElement;
          // duration: 0，不自动关闭
          this.$notify({
            title: '标题名称',
            message: h('i', {
              style: 'color: teal'
            }, 'duration: 0，不自动关闭，自定义消息内容和格式'),
            duration: 0
          });

        } else if (e == 9) {
          //position：自定义弹出位置，top-right/top-left/bottom-right/bottom-left
          this.$notify({
            title: '自定义位置',
            message: '右下角弹出的消息',
            position: 'bottom-right',
            showClose: true
          });

        } else if (e == 10) {
          this.outerVisible = true;

        } else if (e == 11) {
          this.centerDialogVisible = true;
          // } else if (e == 12) {

          // } else if (e == 13) {

          // } else if (e == 14) {

          // } else if (e == 15) {

          // } else if (e == 16) {

          // } else if (e == 17) {

          // } else if (e == 18) {

          // } else if (e == 19) {

          // } else if (e == 20) {

          // } 
          // else {

        }
      },
      handleOpen(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClose(key, keyPath) {
        console.log(key, keyPath);
      },
      handleClick1(row) {
        console.log(row);
      },
      handleClick(tab, event) {
        console.log(tab, event);
      },
      goBack() {
        alert('go back')
      }

    }
  };
</script>
