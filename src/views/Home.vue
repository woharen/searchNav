<style scoped>
    .menu-icon{
        transition: all .3s;
    }
    .rotate-icon{
        transform: rotate(-90deg);
    }
</style>
<template>
    <div>
        <!--左侧菜单栏-->
        <Drawer title="主页" placement="left" :closable="false" v-model="menuState">
            <p>Some contents...</p>
            <p>Some contents...</p>
            <p>Some contents...</p>
        </Drawer>
        <Layout>
            <Header>
                <Row>
                    <Col span="20">
                        <!--<Icon @click.native="collapsedSider" :class="rotateIcon" :style="{margin: '0 20px'}" type="md-menu" size="24"></Icon>-->
                        <Icon @click.native="menuState = true" :style="{margin: '0 20px'}" type="md-menu" size="24"></Icon>
                        <!--<Button @click="menuState = true" type="primary">Open</Button>-->
                    </Col>
                    <Col span="4">
                        <Row type="flex" justify="end">
                            <Col>
                                <Avatar icon="ios-person"/>
                            </Col>
                        </Row>
                    </Col>
                </Row>
            </Header>
            <Content style="min-height: 500px">
                <Row type="flex" justify="center">
                    <Col>
                        <card style="width: 350px">
                            LOGO
                        </card>
                    </Col>
                </Row>
                <BackTop></BackTop>
            </Content>
        </Layout>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                isCollapsed: false,
                menuState: false
            };
        },
        computed: {
            rotateIcon () {
                return [
                    'menu-icon',
                    this.isCollapsed ? 'rotate-icon' : ''
                ];
            }
        },
        methods: {
            collapsedSider: function(){
                this.$refs.side1.toggleCollapse();
            }
        }
    }
</script>
