<template>
  <div id="mapChart" ref="mapChart" style="width:100%; height: 100%"></div>
</template>
<script>
//获取地图数据
import '../../node_modules/echarts/map/js/province/anhui';
import '../../node_modules/echarts/map/js/province/aomen';
import '../../node_modules/echarts/map/js/province/beijing';
import '../../node_modules/echarts/map/js/province/chongqing';
import '../../node_modules/echarts/map/js/province/fujian';
import '../../node_modules/echarts/map/js/province/gansu';
import '../../node_modules/echarts/map/js/province/guangdong';
import '../../node_modules/echarts/map/js/province/guangxi';
import '../../node_modules/echarts/map/js/province/guizhou';
import '../../node_modules/echarts/map/js/province/hainan';
import '../../node_modules/echarts/map/js/province/hebei';
import '../../node_modules/echarts/map/js/province/heilongjiang';
import '../../node_modules/echarts/map/js/province/henan';
import '../../node_modules/echarts/map/js/province/hubei';
import '../../node_modules/echarts/map/js/province/hunan';
import '../../node_modules/echarts/map/js/province/jiangsu';
import '../../node_modules/echarts/map/js/province/jiangxi';
import '../../node_modules/echarts/map/js/province/jilin';
import '../../node_modules/echarts/map/js/province/liaoning';
import '../../node_modules/echarts/map/js/province/neimenggu';
import '../../node_modules/echarts/map/js/province/ningxia';
import '../../node_modules/echarts/map/js/province/qinghai';
import '../../node_modules/echarts/map/js/province/shandong';
import '../../node_modules/echarts/map/js/province/shanghai';
import '../../node_modules/echarts/map/js/province/shanxi';
import '../../node_modules/echarts/map/js/province/shanxi1';
import '../../node_modules/echarts/map/js/province/sichuan';
import '../../node_modules/echarts/map/js/province/taiwan';
import '../../node_modules/echarts/map/js/province/tianjin';
import '../../node_modules/echarts/map/js/province/xianggang';
import '../../node_modules/echarts/map/js/province/xizang';
import '../../node_modules/echarts/map/js/province/yunnan';
import '../../node_modules/echarts/map/js/province/zhejiang';
export default {
  props:{
    province: {
      ename:String,
      name:String
    },
  },
  methods: {
    mapFn() {
      var mapChart = this.$echarts.init(
          document.getElementById("mapChart")
      );
      mapChart.setOption({
        backgroundColor: "", //背景颜色
        title: {
          text: "",
          subtext: "",
          color: "#fff",
          x: "center",
        },
        //是视觉映射组件，用于进行『视觉编码』，也就是将数据映射到视觉元素（视觉通道）。
        visualMap: {
          // 左下角定义 在选中范围中的视觉元素 渐变地区颜色
          type: "piecewise", // 类型为分段型
          top: "bottom",
          // calculable: true, //是否显示拖拽用的手柄（手柄能拖拽调整选中范围）。
          right: 10,
          splitNumber: 6,
          seriesIndex: [0],
          itemWidth: 20, // 每个图元的宽度
          itemGap: 2, // 每两个图元之间的间隔距离，单位为px
          pieces: [
            // 自定义每一段的范围，以及每一段的文字
            {
              gte: 301,
              label: "严重污染(>300)",
              color: "#721424"
            }, // 不指定 max，表示 max 为无限大（Infinity）。
            {
              gte: 201,
              lte: 300,
              label: "重度污染(201-300)",
              color: "#8c1a4b",
            },
            {
              gte: 151,
              lte: 200,
              label: "中度污染(151-200)",
              color: "#e93222",
            },
            {
              gte: 101,
              lte: 150,
              label: "轻度污染(101-150)",
              color: "#ef8433",
            },
            {
              gte: 50,
              lte: 100,
              label: "良(51-100)",
              color: "#fffc53",
            },
            {
              gte: 0,
              lte: 50,
              label: "优(0-50)",
              color: "#67e043"
            }, // 不指定 min，表示 min 为无限大（-Infinity）。
          ],
          textStyle: {
            color: "#BDBDBD",
          },
        },
        // 提示框，鼠标移入
        tooltip: {
          show: true, //鼠标移入是否触发数据
          trigger: "item", //出发方式
          formatter: "{b}-污染指数：{c}",
        },
        //配置地图的数据，并且显示
        series: [
          {
            name: "地图",
            type: "map", //地图种类
            map: this.province.name, //地图类型。
            data: [{"name": "上海市", "value": 226}, {"name": "临沧市", "value": 108}, {"name": "丽江市", "value": 55}, {"name": "保山市", "value": 95}, {"name": "大理白族自治州", "value": 67}, {"name": "德宏傣族景颇族自治州", "value": 141}, {"name": "怒江傈僳族自治州", "value": 56}, {"name": "文山壮族苗族自治州", "value": 107}, {"name": "昆明市", "value": 83}, {"name": "昭通市", "value": 139}, {"name": "普洱市", "value": 92}, {"name": "曲靖市", "value": 103}, {"name": "楚雄彝族自治州", "value": 79}, {"name": "玉溪市", "value": 85}, {"name": "红河哈尼族彝族自治州", "value": 87}, {"name": "西双版纳傣族自治州", "value": 119}, {"name": "迪庆藏族自治州", "value": 46}, {"name": "乌兰察布市", "value": 200}, {"name": "乌海市", "value": 325}, {"name": "兴安盟", "value": 94}, {"name": "包头市", "value": 182}, {"name": "呼伦贝尔市", "value": 73}, {"name": "呼和浩特市", "value": 218}, {"name": "巴彦淖尔市", "value": 170}, {"name": "赤峰市", "value": 143}, {"name": "通辽市", "value": 111}, {"name": "鄂尔多斯市", "value": 136}, {"name": "锡林郭勒盟", "value": 165}, {"name": "阿拉善盟", "value": 283}, {"name": "北京市", "value": 236}, {"name": "云林县", "value": 88}, {"name": "南投县", "value": 70}, {"name": "台东县", "value": 68}, {"name": "台中市", "value": 74}, {"name": "台北市", "value": 100}, {"name": "台南市", "value": 78}, {"name": "嘉义县", "value": 70}, {"name": "基隆市", "value": 96}, {"name": "宜兰县", "value": 102}, {"name": "屏东县", "value": 65}, {"name": "彰化县", "value": 82}, {"name": "新北市", "value": 100}, {"name": "新竹县", "value": 104}, {"name": "桃园市", "value": 102}, {"name": "花莲县", "value": 78}, {"name": "苗栗县", "value": 89}, {"name": "高雄市", "value": 68}, {"name": "吉林市", "value": 141}, {"name": "四平市", "value": 157}, {"name": "延边朝鲜族自治州", "value": 111}, {"name": "松原市", "value": 113}, {"name": "白城市", "value": 106}, {"name": "白山市", "value": 84}, {"name": "辽源市", "value": 150}, {"name": "通化市", "value": 100}, {"name": "长春市", "value": 182}, {"name": "乐山市", "value": 193}, {"name": "内江市", "value": 198}, {"name": "凉山彝族自治州", "value": 65}, {"name": "南充市", "value": 207}, {"name": "宜宾市", "value": 205}, {"name": "巴中市", "value": 175}, {"name": "广元市", "value": 155}, {"name": "广安市", "value": 202}, {"name": "德阳市", "value": 210}, {"name": "成都市", "value": 208}, {"name": "攀枝花市", "value": 104}, {"name": "泸州市", "value": 179}, {"name": "甘孜藏族自治州", "value": 49}, {"name": "眉山市", "value": 193}, {"name": "绵阳市", "value": 154}, {"name": "自贡市", "value": 225}, {"name": "资阳市", "value": 167}, {"name": "达州市", "value": 201}, {"name": "遂宁市", "value": 199}, {"name": "阿坝藏族羌族自治州", "value": 51}, {"name": "雅安市", "value": 150}, {"name": "天津市", "value": 303}, {"name": "中卫市", "value": 221}, {"name": "吴忠市", "value": 163}, {"name": "固原市", "value": 246}, {"name": "石嘴山市", "value": 232}, {"name": "银川市", "value": 396}, {"name": "亳州市", "value": 282}, {"name": "六安市", "value": 222}, {"name": "合肥市", "value": 229}, {"name": "安庆市", "value": 208}, {"name": "宣城市", "value": 171}, {"name": "宿州市", "value": 261}, {"name": "池州市", "value": 200}, {"name": "淮北市", "value": 268}, {"name": "淮南市", "value": 242}, {"name": "滁州市", "value": 238}, {"name": "芜湖市", "value": 253}, {"name": "蚌埠市", "value": 236}, {"name": "铜陵市", "value": 239}, {"name": "阜阳市", "value": 293}, {"name": "马鞍山市", "value": 267}, {"name": "黄山市", "value": 136}, {"name": "东营市", "value": 236}, {"name": "临沂市", "value": 326}, {"name": "威海市", "value": 149}, {"name": "德州市", "value": 281}, {"name": "日照市", "value": 295}, {"name": "枣庄市", "value": 292}, {"name": "泰安市", "value": 286}, {"name": "济南市", "value": 266}, {"name": "济宁市", "value": 267}, {"name": "淄博市", "value": 288}, {"name": "滨州市", "value": 271}, {"name": "潍坊市", "value": 298}, {"name": "烟台市", "value": 207}, {"name": "聊城市", "value": 294}, {"name": "莱芜市", "value": 318}, {"name": "菏泽市", "value": 320}, {"name": "青岛市", "value": 276}, {"name": "临汾市", "value": 251}, {"name": "吕梁市", "value": 152}, {"name": "大同市", "value": 182}, {"name": "太原市", "value": 185}, {"name": "忻州市", "value": 146}, {"name": "晋中市", "value": 217}, {"name": "晋城市", "value": 246}, {"name": "朔州市", "value": 265}, {"name": "运城市", "value": 306}, {"name": "长治市", "value": 218}, {"name": "阳泉市", "value": 220}, {"name": "东莞市", "value": 134}, {"name": "中山市", "value": 143}, {"name": "云浮市", "value": 137}, {"name": "佛山市", "value": 167}, {"name": "广州市", "value": 132}, {"name": "惠州市", "value": 114}, {"name": "揭阳市", "value": 115}, {"name": "梅州市", "value": 117}, {"name": "汕头市", "value": 94}, {"name": "汕尾市", "value": 91}, {"name": "江门市", "value": 126}, {"name": "河源市", "value": 128}, {"name": "深圳市", "value": 123}, {"name": "清远市", "value": 168}, {"name": "湛江市", "value": 106}, {"name": "潮州市", "value": 90}, {"name": "珠海市", "value": 130}, {"name": "肇庆市", "value": 143}, {"name": "茂名市", "value": 150}, {"name": "阳江市", "value": 131}, {"name": "韶关市", "value": 172}, {"name": "北海市", "value": 162}, {"name": "南宁市", "value": 151}, {"name": "崇左市", "value": 144}, {"name": "来宾市", "value": 159}, {"name": "柳州市", "value": 153}, {"name": "桂林市", "value": 185}, {"name": "梧州市", "value": 187}, {"name": "河池市", "value": 142}, {"name": "玉林市", "value": 241}, {"name": "百色市", "value": 155}, {"name": "贵港市", "value": 218}, {"name": "贺州市", "value": 175}, {"name": "钦州市", "value": 182}, {"name": "防城港市", "value": 128}, {"name": "乌鲁木齐市", "value": 136}, {"name": "五家渠市", "value": 299}, {"name": "伊犁哈萨克自治州", "value": 98}, {"name": "克孜勒苏柯尔克孜自治州", "value": 342}, {"name": "克拉玛依市", "value": 264}, {"name": "博尔塔拉蒙古自治州", "value": 103}, {"name": "吐鲁番地区", "value": 283}, {"name": "和田地区", "value": 467}, {"name": "哈密地区", "value": 142}, {"name": "喀什地区", "value": 362}, {"name": "图木舒克市", "value": 488}, {"name": "塔城地区", "value": 184}, {"name": "巴音郭楞蒙古自治州", "value": 437}, {"name": "昌吉回族自治州", "value": 246}, {"name": "石河子市", "value": 403}, {"name": "阿克苏地区", "value": 415}, {"name": "阿勒泰地区", "value": 194}, {"name": "阿拉尔市", "value": 420}, {"name": "南京市", "value": 256}, {"name": "南通市", "value": 227}, {"name": "宿迁市", "value": 252}, {"name": "常州市", "value": 246}, {"name": "徐州市", "value": 289}, {"name": "扬州市", "value": 247}, {"name": "无锡市", "value": 239}, {"name": "泰州市", "value": 236}, {"name": "淮安市", "value": 241}, {"name": "盐城市", "value": 233}, {"name": "苏州市", "value": 237}, {"name": "连云港市", "value": 246}, {"name": "镇江市", "value": 262}, {"name": "上饶市", "value": 153}, {"name": "九江市", "value": 185}, {"name": "南昌市", "value": 149}, {"name": "吉安市", "value": 188}, {"name": "宜春市", "value": 184}, {"name": "抚州市", "value": 160}, {"name": "新余市", "value": 206}, {"name": "景德镇市", "value": 142}, {"name": "萍乡市", "value": 250}, {"name": "赣州市", "value": 160}, {"name": "鹰潭市", "value": 170}, {"name": "保定市", "value": 244}, {"name": "唐山市", "value": 297}, {"name": "廊坊市", "value": 327}, {"name": "张家口市", "value": 136}, {"name": "承德市", "value": 162}, {"name": "沧州市", "value": 284}, {"name": "石家庄市", "value": 293}, {"name": "秦皇岛市", "value": 255}, {"name": "衡水市", "value": 292}, {"name": "邢台市", "value": 319}, {"name": "邯郸市", "value": 328}, {"name": "三门峡市", "value": 220}, {"name": "信阳市", "value": 283}, {"name": "南阳市", "value": 255}, {"name": "周口市", "value": 330}, {"name": "商丘市", "value": 311}, {"name": "安阳市", "value": 305}, {"name": "平顶山市", "value": 299}, {"name": "开封市", "value": 346}, {"name": "新乡市", "value": 285}, {"name": "洛阳市", "value": 251}, {"name": "济源市", "value": 251}, {"name": "漯河市", "value": 394}, {"name": "濮阳市", "value": 332}, {"name": "焦作市", "value": 300}, {"name": "许昌市", "value": 368}, {"name": "郑州市", "value": 359}, {"name": "驻马店市", "value": 332}, {"name": "鹤壁市", "value": 313}, {"name": "丽水市", "value": 114}, {"name": "台州市", "value": 116}, {"name": "嘉兴市", "value": 235}, {"name": "宁波市", "value": 172}, {"name": "杭州市", "value": 140}, {"name": "温州市", "value": 118}, {"name": "湖州市", "value": 199}, {"name": "绍兴市", "value": 167}, {"name": "舟山市", "value": 112}, {"name": "衢州市", "value": 135}, {"name": "金华市", "value": 130}, {"name": "三亚市", "value": 64}, {"name": "东方市", "value": 66}, {"name": "临高县", "value": 77}, {"name": "乐东黎族自治县", "value": 63}, {"name": "五指山市", "value": 72}, {"name": "保亭黎族苗族自治县", "value": 64}, {"name": "儋州市", "value": 78}, {"name": "定安县", "value": 76}, {"name": "屯昌县", "value": 77}, {"name": "文昌市", "value": 72}, {"name": "昌江黎族自治县", "value": 73}, {"name": "海口市", "value": 75}, {"name": "澄迈县", "value": 84}, {"name": "琼中黎族苗族自治县", "value": 77}, {"name": "琼海市", "value": 72}, {"name": "白沙黎族自治县", "value": 74}, {"name": "陵水黎族自治县", "value": 65}, {"name": "仙桃市", "value": 236}, {"name": "十堰市", "value": 186}, {"name": "咸宁市", "value": 237}, {"name": "天门市", "value": 237}, {"name": "孝感市", "value": 255}, {"name": "宜昌市", "value": 200}, {"name": "恩施土家族苗族自治州", "value": 155}, {"name": "武汉市", "value": 242}, {"name": "潜江市", "value": 265}, {"name": "神农架林区", "value": 123}, {"name": "荆州市", "value": 229}, {"name": "荆门市", "value": 263}, {"name": "襄阳市", "value": 248}, {"name": "鄂州市", "value": 228}, {"name": "随州市", "value": 262}, {"name": "黄冈市", "value": 203}, {"name": "黄石市", "value": 215}, {"name": "娄底市", "value": 198}, {"name": "岳阳市", "value": 214}, {"name": "常德市", "value": 204}, {"name": "张家界市", "value": 163}, {"name": "怀化市", "value": 146}, {"name": "株洲市", "value": 229}, {"name": "永州市", "value": 200}, {"name": "湘潭市", "value": 262}, {"name": "湘西土家族苗族自治州", "value": 144}, {"name": "益阳市", "value": 209}, {"name": "衡阳市", "value": 231}, {"name": "邵阳市", "value": 192}, {"name": "郴州市", "value": 223}, {"name": "长沙市", "value": 230}, {"name": "临夏回族自治州", "value": 314}, {"name": "兰州市", "value": 232}, {"name": "嘉峪关市", "value": 393}, {"name": "天水市", "value": 171}, {"name": "定西市", "value": 155}, {"name": "平凉市", "value": 321}, {"name": "庆阳市", "value": 147}, {"name": "张掖市", "value": 166}, {"name": "武威市", "value": 196}, {"name": "甘南藏族自治州", "value": 89}, {"name": "白银市", "value": 199}, {"name": "酒泉市", "value": 356}, {"name": "金昌市", "value": 364}, {"name": "陇南市", "value": 129}, {"name": "三明市", "value": 133}, {"name": "南平市", "value": 126}, {"name": "厦门市", "value": 106}, {"name": "宁德市", "value": 102}, {"name": "泉州市", "value": 93}, {"name": "漳州市", "value": 85}, {"name": "福州市", "value": 94}, {"name": "莆田市", "value": 104}, {"name": "龙岩市", "value": 142}, {"name": "山南地区", "value": 46}, {"name": "拉萨市", "value": 62}, {"name": "日喀则地区", "value": 50}, {"name": "昌都地区", "value": 48}, {"name": "林芝地区", "value": 44}, {"name": "那曲地区", "value": 51}, {"name": "阿里地区", "value": 44}, {"name": "六盘水市", "value": 123}, {"name": "安顺市", "value": 134}, {"name": "毕节市", "value": 122}, {"name": "贵阳市", "value": 146}, {"name": "遵义市", "value": 142}, {"name": "铜仁市", "value": 131}, {"name": "黔东南苗族侗族自治州", "value": 121}, {"name": "黔南布依族苗族自治州", "value": 123}, {"name": "黔西南布依族苗族自治州", "value": 123}, {"name": "丹东市", "value": 103}, {"name": "大连市", "value": 163}, {"name": "抚顺市", "value": 115}, {"name": "朝阳市", "value": 153}, {"name": "本溪市", "value": 109}, {"name": "沈阳市", "value": 166}, {"name": "盘锦市", "value": 194}, {"name": "营口市", "value": 139}, {"name": "葫芦岛市", "value": 224}, {"name": "辽阳市", "value": 142}, {"name": "铁岭市", "value": 162}, {"name": "锦州市", "value": 206}, {"name": "阜新市", "value": 161}, {"name": "鞍山市", "value": 142}, {"name": "重庆市", "value": 142}, {"name": "咸阳市", "value": 293}, {"name": "商洛市", "value": 164}, {"name": "安康市", "value": 146}, {"name": "宝鸡市", "value": 270}, {"name": "延安市", "value": 140}, {"name": "榆林市", "value": 161}, {"name": "汉中市", "value": 155}, {"name": "渭南市", "value": 253}, {"name": "西安市", "value": 277}, {"name": "铜川市", "value": 174}, {"name": "果洛藏族自治州", "value": 57}, {"name": "海东地区", "value": 115}, {"name": "海北藏族自治州", "value": 64}, {"name": "海南藏族自治州", "value": 61}, {"name": "海西蒙古族藏族自治州", "value": 114}, {"name": "玉树藏族自治州", "value": 72}, {"name": "西宁市", "value": 168}, {"name": "黄南藏族自治州", "value": 68}, {"name": "香港特别行政区", "value": 110}, {"name": "七台河市", "value": 151}, {"name": "伊春市", "value": 75}, {"name": "佳木斯市", "value": 155}, {"name": "双鸭山市", "value": 144}, {"name": "哈尔滨市", "value": 150}, {"name": "大兴安岭地区", "value": 89}, {"name": "大庆市", "value": 165}, {"name": "牡丹江市", "value": 105}, {"name": "绥化市", "value": 159}, {"name": "鸡西市", "value": 102}, {"name": "鹤岗市", "value": 97}, {"name": "黑河市", "value": 82}, {"name": "齐齐哈尔市", "value": 138}],
            itemStyle: {
              normal: {
                label: {
                  show: true, //默认是否显示省份名称
                },
                areaStyle: {
                  color: "#FAFAFA", //默认的地图板块颜色
                },
                borderWidth: 1,
                borderColor: "#D9D9D9",
              },
              //地图区域的多边形 图形样式。
              emphasis: {
                label: {
                  show: true, //选中状态是否显示省份名称
                },
                areaStyle: {
                  color: "#90c31d", //选中状态的地图板块颜色
                },
              },
            },
            zoom: 1, //放大比例
            label: {
              //图形上的文本标签，可用于说明图形的一些数据信息
              show: true,
            },
          },
          {
            type: "scatter",
            showEffectOn: "render", //配置什么时候显示特效
            coordinateSystem: "geo", //该系列使用的坐标系
            symbolSize: 10, //标记的大小
            data: [{name: "宜昌", value: [111.3, 30.7, 130]}],
            zlevel: 99999,
          },
        ],
      });

      mapChart.on("dblclick",() => {
        this.changeChartData()

      })

      window.addEventListener("resize", () => {
        // 自动渲染echarts
        mapChart.resize();
      });
    },

    changeChartData(){
      this.$emit("backToChinaMap");
    }

  },
  mounted() {
    this.mapFn();
  },
};
</script>
<style scoped>
.chinaecharts {
  width: 100%;
  height: 500px;
}

/*#mapChart {*/
/*  width: 100%;*/
/*  height: 500px;*/
/*}*/
</style>
