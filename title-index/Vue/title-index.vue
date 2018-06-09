<template id="title-index">
	 <div class="title-index" :class="[noselect,select]" @click="ti_select" @mousemove="ti_move" @mouseout="ti_moveout">
		 <img class="ti-img noselect" :src="img"></img>
		 <div class="ti-title font-xirod noselect">{{title}}</div>
		 <div class="ti-em-select" :class="hide">Get</div>
		 <div class="ti-context noselect">{{context}}</div>
	 </div>
</template>

<script>
export default {
	name: 'title-index',
	props:['img','title','context','type','index'],
	data(){
		return {
			noselect:'ti-noselect',	//默认不选择状态
			select:'',
			hide:'dis-hide'
		}
	},
	methods:{
		ti_select:function(){
			if(this.type == 'click'){//鼠标点击后改变状态
				if(this.noselect==''){			//不选中
				this.$emit('noselect',this.index);
					this.noselect = 'ti-noselect';
					this.select = '';
					this.hide = 'dis-hide';
				}else{							//选中
				this.$emit('select',this.index);
					this.noselect = '';
					this.select = 'ti-select';  
					this.hide = '';
				}
			}
		},
		ti_move:function(){
			if(this.type == 'move'){//鼠标经过后改变状态
				this.noselect = '';
				this.select = 'ti-select';
				this.hide = '';
			}
		},
		ti_moveout:function(){
			if(this.type == 'move'){//鼠标经过后改变状态
				this.noselect = 'ti-noselect';
				this.select = '';
				this.hide = 'dis-hide';
			}
		}
	}
}
</script>

<style>
/*标题索引组件*/
.title-index{
	width:450px;
	height:90px;
	margin-bottom: 10px; 
	margin-right: 10px; 
	padding: 15px 15px 15px 7px; 
	line-height: 22px; 
	border-width:1px;
	border-color:#D5D5D5;
	border-style:solid;
	border-left: 7px solid #c7c7c7; 
	border-radius: 0 2px 2px 0; 
	background-color: #ffffff;
	box-shadow: #D5D5D5 3px 3px 9px 0px;/*浅灰 x轴偏移 y轴偏移 半径*/
	cursor:default;
	position:relative;
	float:left;
}
/*标题索引组件 标题*/
.ti-title{
	display: inline-block;
	clear:both;
	font-weight:bold;
	font-family:”微软雅黑”;
	font-size: 16;
	z-index:2;
	margin-left:-20px;
	cursor:default;
}
/*标题索引组件 内容*/
.ti-context{
	margin-top:8px;
	font-family:”微软雅黑”;
	font-size: 14;
	letter-spacing:0.7;
	line-height:1.4;
	overflow:hidden;
	z-index:2;
	cursor:default;
}
/*标题索引组件 左缩略图*/
.ti-img{
	float:left;
	width:60px;
	height:60px;
	padding-bottom:30px;
	padding-right:10px;
	z-index:2;
}
/*标题索引组件 右上选中*/
.ti-em-select{
	position:relative;
	right:-75%;
	top:-10px;
	font-family:xirod;
	font-size: 14;
	color:#3299FF;
	z-index:2;
	float:left;
	cursor:default;
}
/*标题索引组件 没选中 深灰*/
.ti-noselect{
	border-left: 7px solid #c7c7c7; 
	border-color:#D5D5D5;
}
/*标题索引组件 被选中 深蓝*/
.ti-select{
	border-left: 7px solid #3299FF; 
	border-color:#3299FF;
}
/*标题索引组件 右上角Get隐藏*/
.dis-hide{
	visibility:hidden;
}
/*标题索引组件 右上角Get显示*/
.dis-show{
	visibility:none;
}
/*不允许选中*/
.noselect {
	-webkit-touch-callout: none; /* iOS Safari */
	-webkit-user-select: none; /* Chrome/Safari/Opera */
	-khtml-user-select: none; /* Konqueror */
	-moz-user-select: none; /* Firefox */
	-ms-user-select: none; /* Internet Explorer/Edge */
	user-select: none; /* Non-prefixed version, currently
	not supported by any browser */
}
</style>