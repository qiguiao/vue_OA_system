### 三鑫智慧社区
前端时间学了vue，后来实在觉得技术总得实践，就直接上手vue2.0。然后花了将近两周时间做了一个后台管理系统的小项目。一开始觉得项目比较小，没必要用vuex所以就没有使用，但是后来发现数据流传输有点麻烦，后续会使用vuex。
* 背景

    > 通过智慧社区建设，提升社区工作人员工作效率，减轻其工作负担，让工作人员
    能够腾出更多时间服务居民，有效提高居民对社区、政府的满意度；创新、优化公共
    服务模式及流程，简化办事程序，居民办事便捷了。

* 技术栈

    - webpack+vue+vuex（核心框架）
    - [express](https://www.npmjs.com/package/express)（用于模拟后台服务 模拟接口）
    - [element ui](https://www.npmjs.com/package/element-ui)（用于完成一些基本的效果）
     - [ jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken)（用户基本信息加密）
    - [ mockjs](https://www.npmjs.com/package/mockjs)（生成mock数据）
    - [ axios](https://www.npmjs.com/package/axios)（请求）
   

* 功能分析与设计

   - login (登陆页面)
     - 通过用户输入的账号和密码进行 “post” 发送到后台模拟接口,进行验证,如果用户存在已知的数据中,直接进入"index"显示路由页面,否则跳转至“register”提示用户进行注册。
   - register (注册页面)
     - 用户没有账号密码的情况下,在登陆页面要显示注册的按钮,提示用户进行注册,注册完成之后,跳会 “login” 进行登陆。
   - index(路由切换页面)
     - 分为 “一口式受理平台”, “网格化管理平台” , “公共服务平台” 三个模块进行开发。
     - “一口式受理平台”: 可以让用户进行报名,报名之后把用户信息写入数据,让用户具有参赛资格,同时管理员可以管理用户,如果有用户不想参加活动,可以进行删除。
     - “公共服务平台”:分为信息管理,和活动管理,信息管理中可以把用户填写的数据取出来,发送给后台,写入数据。
     活动管理中的 邀请居民把参加的用户进行页面渲染,分页,以及用户进行备注, 基本信息中用到图片上传,城市渲染,添加栏目功能,编辑栏目名称,保存并发布之后传送到后台写入数据。
   - main (页面导航)
     - 通过导航列表,进行路由切换,以及侧边栏数据进行更新。
   - menu (侧边栏)
     - 这个区域是通过导航点击之后渲染上去的,导航每个标题切换的时候,数据进行更新变化,重新渲染。

* 开发过程中问题

    - 路由跳转时个人认为 element ui组件中可以直接在标签上如 :to="{name:'路由名字'}",后来发现组件中的标签无法解析,后来经过与朋友讨论,抛开组件,可以加入<router-link :to="{name:'路由名字'}"></router-link>,或者加入点击事件,进行 this.$router.push({name:'路由名字'}),可以解决路由跳转问题。
    - 图片上传,添加栏目时,一开始直接向后台发送请求,从数据中进行添加栏目,后来发现数据传送有些麻烦,不利于管理和更好的控制,所以项目中添加了vuex更好的进行数据管理。
    - 弹框的选择是一件非常重要的事情,在“邀请居民”模块中需要为居民进行备注,这个一开始选用的是 element ui 中的MessageBox 弹框 , 需求是要取出文本框中的内容,发送给后台,这个组件的操作全都是放在一个回调函数中类似于 Promise ,上手不太方便,后来经过深思熟虑,采用了Dialog 对话框,直接在结构中加入 input 标签 v-modle 绑定值,取出数据发送给后台,写入数据中,完成了效果.

* 项目运行

   - npm run dev 

* 说明

   - 需要改进的有很多，请大家可以多提提意见。后续我会不断改进。

