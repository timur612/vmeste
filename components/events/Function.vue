<template>
    <scroll-view :content-container-style="{contentContainer: {
        paddingVertical: 20
    }}">
    <view style="marginTop:25">
        <view class="header">
            <text class="text"> 
                вместе
            </text>
        </view>

        <view style="marginTop:30;marginLeft:15">
            <touchable-opacity style="marginBottom:15" :on-press="goToBack">
                <image
                    :source="require('../../assets/Events/arrow_left.png')"
                />
            </touchable-opacity>
            <view class="card" v-for="(event,key) in events" :key="key">
                <touchable-opacity >
                    <text class="cardtext"> {{event.heading}} </text>
                    <view style="flexDirection:row;marginLeft:8;">
                        <image
                            style="height:17;width:17"
                            :source="require('../../assets/Main/calendar.png')"
                        />
                        <text style="color:#7E7E7E">
                            07.04.22, 13:15 - 08.04.22, 13:15  
                        </text>
                    </view>

                    <view style="flexDirection:row;marginLeft:8;marginBottom:3;">
                        <image
                            style="height:17;width:17"
                            :source="require('../../assets/Main/marker.png')"
                        />
                        <text style="color:#7E7E7E">
                            г Якутск, ул Кулаковского, д 34/5 
                        </text>
                    </view>
                    <view style="flexDirection:row;margin-top:4">
                        <view class="badgetext">
                            <text style="color:white;fontSize:12;">{{event.badge}}</text>
                        </view>
                        <view class="badgetext">
                            <text style="color:white;fontSize:12;"> {{event.score}} </text>
                        </view>
                    </view>
                    
                </touchable-opacity >
            </view>
        </view>
    </view>
    </scroll-view>
</template>

<script>
export default {
    data(){
        return{
            events:[ {badge:'Гражданство РФ', score: '18+', heading: 'Волонтер штаба'},
                        {badge:'Гражданство РФ', score: '18+', heading: 'Волонтер штаба'},
                        

                ],
        }
    },
    props: {
            navigation: {
            type: Object
            }
        },
        methods: {
            goToBack: function() {
                this.navigation.navigate("Event");
            },
        }
}
</script>

<style scoped>
    /* COPY */
    .header{
        flex-direction:row;
    }
    .text{
        font-size:35;
        color:#75D811;
        font-weight: bold;
    }
    /* COPY */

    .card{
        /* flex-direction:row; */
        width:330;
        border-right-width:1;
        border-left-width:1;
        padding-bottom: 5   ;
        border-top-width:1;
        border-bottom-width:1;
        border-radius:10;
        border-color:#75D811;
        margin-bottom:10;
    }
    .cardtext{
        width: 250;
        font-size:15;
        font-weight: bold;
        margin-top:5;
        margin-left:5;
        margin-bottom:7;
    }
    .badgetext{
        background-color:#75D811;
        border-radius:5;
        padding:5;
        margin-left:10;
        margin-top:5;
    }
</style>