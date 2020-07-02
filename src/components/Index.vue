<template>
    <div class="infinite-list-wrapper" style="overflow:auto">
        <ul class="list" v-infinite-scroll="load" infinite-scroll-disabled="disabled" v-for="(o, index) in count" :key="o" :offset="index > 0 ? count : 0">
            <el-row>
                <el-col>
                    <el-card :body-style="{ padding: '30px' }">
                        <div style="padding: 14px;">
                            <span><el-link href="https://element.eleme.io" type="primary">XXX详解</el-link></span>
                            <div class="bottom clear-fix">
                                <time class="time">{{ currentDate }}</time>
                            </div>
                        </div>
                    </el-card>
                </el-col>
            </el-row>
        </ul>
        <p v-if="loading">Loading</p>
        <p v-if="noMore">No More</p>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                currentDate: new Date(),
                count: 10,
                loading: false
            };
        },
        computed: {
            noMore() {
                return this.count >= 100
            },
            disabled() {
                return this.loading || this.noMore
            }
        },
        methods: {
            load() {
                this.loading = true;
                setTimeout(() => {
                    this.count += 2;
                    this.loading = false
                }, 2000)
            }
        }
    }
</script>

<style>
    .time {
        font-size: 13px;
        color: #999;
    }

    .bottom {
        margin-top: 13px;
        line-height: 12px;
    }

    .button {
        padding: 0;
        float: right;
    }

    .image {
        width: 100%;
        display: block;
    }

    .clear-fix:before,
    .clear-fix:after {
        display: table;
        content: "";
    }

    .clear-fix:after {
        clear: both
    }
</style>