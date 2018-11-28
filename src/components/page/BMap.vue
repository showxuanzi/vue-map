<!-- 页面模版 -->
<template>
  <div>
    <!--container-->
    <div id="allmap" 
            style="
                width: 100%; 
                height:1000px; 
                border: 1px solid gray;
                overflow:hidden;">
        </div>
    <!--container end-->
  </div>
</template>
<script>
import BMap from 'BMap'
export default {
  data: () => ({
    
  }),
  created () {
    
  },
  mounted () {
    // 百度地图API功能  
  var map = new BMap.Map("allmap");
  map.centerAndZoom(new BMap.Point(117.162605,39.166283), 15);
  map.enableScrollWheelZoom();   //启用滚轮放大缩小，默认禁用
  map.enableContinuousZoom();    //启用地图惯性拖拽，默认禁用
    // 地图自定义样式
//    map.setMapStyle({
//        styleJson: [{
//            "featureType": "water",
//            "elementType": "all",
//            "stylers": {
//                "color": "#044161"
//            }
//        }, {
//            "featureType": "land",
//            "elementType": "all",
//            "stylers": {
//                "color": "#091934"
//            }
//        }, {
//            "featureType": "boundary",
//            "elementType": "geometry",
//            "stylers": {
//                "color": "#064f85"
//            }
//        }, {
//            "featureType": "railway",
//            "elementType": "all",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "highway",
//            "elementType": "geometry",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "highway",
//            "elementType": "geometry.fill",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "highway",
//            "elementType": "labels",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "arterial",
//            "elementType": "geometry",
//            "stylers": {
//                "color": "#004981",
//                "lightness": -39
//            }
//        }, {
//            "featureType": "arterial",
//            "elementType": "geometry.fill",
//            "stylers": {
//                "color": "#00508b"
//            }
//        }, {
//            "featureType": "poi",
//            "elementType": "all",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "green",
//            "elementType": "all",
//            "stylers": {
//                "color": "#056197",
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "subway",
//            "elementType": "all",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "manmade",
//            "elementType": "all",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "local",
//            "elementType": "all",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "arterial",
//            "elementType": "labels",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "boundary",
//            "elementType": "geometry.fill",
//            "stylers": {
//                "color": "#029fd4"
//            }
//        }, {
//            "featureType": "building",
//            "elementType": "all",
//            "stylers": {
//                "color": "#1a5787"
//            }
//        }, {
//            "featureType": "label",
//            "elementType": "all",
//            "stylers": {
//                "visibility": "off"
//            }
//        }, {
//            "featureType": "poi",
//            "elementType": "labels.text.fill",
//            "stylers": {
//                "color": "#ffffff"
//            }
//        }, {
//            "featureType": "poi",
//            "elementType": "labels.text.stroke",
//            "stylers": {
//                "color": "#1e1c1c"
//            }
//        }, {
//            "featureType": "administrative",
//            "elementType": "labels",
//            "stylers": {
//                "visibility": "on"
//            }
//        }, {
//            "featureType": "road",
//            "elementType": "labels",
//            "stylers": {
//                "visibility": "off"
//            }
//        }]
//    });
  var data_info = [
                     [117.162605,39.166283,"地址：天津市红桥区湘潭道1号","image/qigong.jpg","启工科技创新中心","20℃","20%","32","39","54","28","0.6","54"],
           [117.16998,39.164265,"地址：天津市红桥区西站前街1号 ","image/qigong.jpg","天津西站","wd-2","sd-2","pm2.5-2","pm10-2","o2-2","no2-2","co-2","o3-2"],
           [117.216853,39.142488,"地址：天津市河北区新纬路1号 ","image/qigong.jpg","地点3","wd-3","sd-3","pm2.5-3","pm10-3","o2-3","no2-3","co-3","o3-3"]
          ];
  var opts = {
        width : 600,     // 信息窗口宽度
        height: 300,     // 信息窗口高度
        // title : "信息窗口" , // 信息窗口标题
        enableMessage:true//设置允许信息窗发送短息
         };
  for(var i=0;i<data_info.length;i++){
    var marker = new BMap.Marker(new BMap.Point(data_info[i][0],data_info[i][1]));  // 创建标注
        var content = '<div id="box">'
                    +'<div class="box">'
                    +'<h3 class="box-title">'+ data_info[i][4]  +'</h3>'
                    +'<div class="clear">'
                    +'<div class="box-img">'
                    +'<img src="'+ data_info[i][3] +'">'
                    +'</div>'
                    +'<div class="box-para">'
                    +'<ul>'
                    +'<li><span>温度：</span><strong>'+ data_info[i][5]  +'</strong></li>'
                    +'<li><span>湿度：</span><strong>'+ data_info[i][6]  +'</strong></li>'
                    +'<li><span>PM2.5：</span><strong>'+ data_info[i][7]  +'</strong></li>'
                    +'<li><span>PM10：</span><strong>'+ data_info[i][8]  +'</strong></li>'
                    +'<li><span>SO2：</span><strong>'+ data_info[i][9]  +'</strong></li>'
                    +'<li><span>NO2：</span><strong>'+ data_info[i][10]  +'</strong></li>'
                    +'<li><span>CO：</span><strong>'+ data_info[i][11]  +'</strong></li>'
                    +'<li><span>O3：</span><strong>'+ data_info[i][12]  +'</strong></li>'
                    +'</ul>'
                    +'</div>'
                    +'</div>'
                    +'<div class="box-address">'+ data_info[i][2] +'</div>'
                    +'</div>'
                    +'</div>';
    map.addOverlay(marker);               // 将标注添加到地图中
    addClickHandler(content,marker);
  }
  function addClickHandler(content,marker){
    marker.addEventListener("click",function(e){
      openInfo(content,e)}
    );
  }
  function openInfo(content,e){
    var p = e.target;
    var point = new BMap.Point(p.getPosition().lng, p.getPosition().lat);
    var infoWindow = new BMap.InfoWindow(content,opts);  // 创建信息窗口对象 
    map.openInfoWindow(infoWindow,point); //开启信息窗口
  }
  },
  methods: {
    
    
  }
}
</script>
<style>
  /* 去掉地图左下角的百度LOGO */
  .anchorBL {
    display:none
  }
  body, html {width: 100%;height: 100%;margin:0;font-family:"微软雅黑";}
        body,html,head,header,section,footer,h1,h2,h3,h4,h5,h6,div,p,a,img,ul,li,ol,dl,dd,dt,form,input,button,textarea,select,option,table,thead,tbody,tfoot,th,tr,td,span{
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            -webkit-box-sizing: border-box;
        }
        li{
            list-style: none;
        }
    #allmap{width:100%;height:500px;}
        .box{
            width: 600px;
            padding: 10px;
            border-radius: 20px;
        }
        .box-title{
            line-height: 50px;
            color: #f80b0b;
        }
        .clear:after{
            display: block;
            content: ".";
            clear: both;
            overflow: hidden;
            visibility: hidden;
        }
        .box-img{
            float: left;

        }
        .box-img>img{
            width: 210px;
            height: 140px;
            margin-top: 15px;
        }
        .box-para{
            float: left;
            width: 340px;
            padding-left: 20px;
        }
        .box-para>ul>li{
            width: 50%;
            float: left;
            line-height: 40px;
            border-bottom: 1px dashed #ccc;
        }
        .box-para>ul>li>strong{
            color: #26c4f9;
        }
        .box-address{
            text-align: center;
            line-height: 40px;
        }
</style>
