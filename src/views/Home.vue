<style scoped>
</style>
<template>
    <div>
        <!--左侧菜单栏-->
        <Drawer title="XX搜索" placement="left" :closable="false" :mask="false" v-model="menuConfig.isActive">
            <list>
                <ListItem v-for="(item, index) in menuConfig.items">
                    <ListItemMeta :title="item.title" :description="item.description">
                        <template slot="avatar">
                            <Avatar v-if="'' == item.avatar" icon="md-book" />
                            <Avatar v-else :src="item.avatar" @on-error="avatarError"/>
                        </template>
                    </ListItemMeta>
                </ListItem>
            </list>
        </Drawer>
        <div @click="menuConfig.isActive = false">
            <Layout>
                <Header>
                    <Row>
                        <!--左侧菜单-->
                        <Col span="20">
                            <Icon @click.stop.native="menuConfig.isActive = true" type="md-menu" size="24" color="#ffffff"></Icon>
                        </Col>
                        <!--右侧头像-->
                        <Col span="4">
                            <Row type="flex" justify="end">
                                <Col>
                                    <Dropdown trigger="click" style="margin-left: 20px"  @on-click="chickAvatar">
                                        <a href="javascript:void(0)">
                                            <Avatar v-if="'' == userInfo.avatar" style="background-color: #87d068" icon="ios-person" />
                                            <Avatar v-else style="background-color: #87d068">{{userInfo.avatar}}</Avatar>
                                        </a>
                                        <DropdownMenu slot="list">
                                            <DropdownItem name="info">个人信息</DropdownItem>
                                            <DropdownItem name="outLogin">注销登录</DropdownItem>
                                        </DropdownMenu>
                                    </Dropdown>
                                </Col>
                            </Row>
                        </Col>
                    </Row>
                </Header>
                <Content style="min-height: 500px">
                    <Row type="flex" justify="center" style="margin-top: 40px">
                        <Col>
                            <card style="width: 350px">
                                LOGO
                            </card>
                        </Col>
                    </Row>
                    <Row type="flex" justify="center" style="margin-top: 40px">
                        <Col>
                            <Input style="width: 500px" search enter-button placeholder="Enter something..." maxlength="255" size="large"/>
                        </Col>
                    </Row>
                    <Row type="flex" justify="center" style="margin-top: 40px;">
                        <Col span="4">
                            <card style="width: 100%;">
                                LOGO
                            </card>
                        </Col>
                        <Col span="4">
                            <card style="width: 100%;">
                                LOGO
                            </card>
                        </Col>
                        <Col span="4">
                            <card style="width: 100%;">
                                LOGO
                            </card>
                        </Col>
                    </Row>
                    <Row type="flex" justify="center" style="margin-top: 40px">
                        <Col span="4">
                            <card style="width: 100%;">
                                LOGO
                            </card>
                        </Col>
                        <Col span="4">
                            <card style="width: 100%;">
                                LOGO
                            </card>
                        </Col>
                        <Col span="4">
                            <card style="width: 100%;">
                                LOGO
                            </card>
                        </Col>
                    </Row>
                    <BackTop></BackTop>
                </Content>
            </Layout>
        </div>
    </div>
</template>
<script>

    export default {
        data() {
            return {
                //菜单栏
                menuConfig: {
                    //菜单栏状态 true:显示 false:隐藏
                    isActive: false,
                    items: []
                },
                userInfo: {
                    name: "",
                    avatar: "admin"
                }

            };
        },
        created: function() {
            this.menuConfig.items.push({
                title: "收藏",
                description: "小收藏啦",
                avatar: ""
            });
            this.menuConfig.items.push({
                title: "其他",
                description: "其他",
                avatar: "xxxx"
            });
            this.menuConfig.items.push({
                title: "关于",
                description: "基本介绍",
                avatar: "https://dev-file.iviewui.com/userinfoPDvn9gKWYihR24SpgC319vXY8qniCqj4/avatar"
            });
        },
        methods: {
            closeMenuDrawer: function() {
                this.menuConfig.isActive = false;
            },
            //图片不存在错误
            avatarError: function (event) {
                event.target.outerHTML = '<span data-v-fae5bece="" class="ivu-avatar ivu-avatar-circle ivu-avatar-icon ivu-avatar-default"><i class="ivu-icon ivu-icon-md-book"></i></span>';
            },
            // 头像下拉点击事件
            chickAvatar: function (value) {
                window.console.log(value);
            }
        }
    }
</script>
