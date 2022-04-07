<template>
<scroll-view :content-container-style="{contentContainer: {
        
    }}">
    <view style="marginTop:10%">
        <view style="marginTop:25%">
            <image
                style="marginLeft:12%"
                :source="require('../assets/About/logo.png')"
            />
            <text style="marginLeft:25%;marginTop:5%;color:#7E7E7E">Версия приложения 0.0.15</text>
        </view>
        
        <view style="marginTop:30%;padding:5%">
            <touchable-opacity class="btn">
                <image
                    :source="require('../assets/About/rect.png')"
                />
                <text style="color:white;marginLeft:3%;">Единая карта волонтера</text>
            </touchable-opacity>
            <touchable-opacity class="btn">
                <image
                    :source="require('../assets/About/info.png')"
                />
                <text style="color:white;marginLeft:3%;">О нас</text>
            </touchable-opacity>
            <touchable-opacity class="btn">
                <image
                    :source="require('../assets/About/mail.png')"
                />
                <text style="color:white;marginLeft:3%;">Оставить отзыв</text>
            </touchable-opacity>
            <touchable-opacity class="btn">
                <image
                    :source="require('../assets/About/star.png')"
                />
                <text style="color:white;marginLeft:3%;">Связаться с техподдержкой</text>
            </touchable-opacity>
        </view>
    </view>
</scroll-view>
</template>

<style scoped>
    .btn{
        background-color: #75D811;
        padding:5%;
        border-radius: 10;
        flex-direction: row;
        margin-bottom: 3%;
    }
</style>