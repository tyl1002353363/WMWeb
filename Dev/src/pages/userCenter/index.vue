<template>
    <div class="upload-app">
        <Tabs>
            <TabPane label="基础信息">
                <div class="my-info-form">
                    <form >
                        <VMacInput title="账号" :value="userInfo.account" :help="nameHelp" readonly/>
                        <VMacInput title="用户名" v-model="userInfo.name" :help="nameHelp"/>
                        <VMacInput title="邮箱" v-model="userInfo.email"  @keyup="say($event)" required/>
                        <VMacInput title="权限" v-model="userInfo.power"  @keyup="say($event)" readonly/>

                        <Button @click="updateInfo" long>保存</Button>
                    </form>
                    
                </div>
            </TabPane>

            <TabPane label="头像管理">
                <form action="http://localhost:9085/upload" method="post" enctype="multipart/form-data">
                    <p><input type="file" name="img" multiple></p>
                    <p><input type="file" name="video"></p>
                    <p><input type="text" name="name"></p>
                    <p><input type="password" name="pswd"></p>
                    <p><input type="submit"></p>
                </form>
            </TabPane>
            
            <TabPane label="密码管理">
                <div class="my-info-pass">
                    <form action="">
                        <p>
                            <VMacInput title="密码" v-model="pwd"  type="password" @blur="verifyPwd" :help="pwdHelp"/>
                        </p>
                        <p>
                            <VMacInput title="确认密码" v-model="surepwd" type="password" @blur="verifyPwdSure" :help="surePwdHelp"/>
                        </p>
                        <Button @click="updatePwd" long>保存</Button>
                    </form>
                </div>
            </TabPane>
        </Tabs>
    </div>
</template>

<style lang="less" scoped src="./layout.less"></style>
<script src="./main.js"></script>