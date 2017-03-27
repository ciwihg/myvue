<template>
  <div>
<div v-bind:class="{headfixed:headfix}">
  <div class="container" >
    <div class="nav">
      <ul class="container_itemlist">
        <li><a href="#">Sign in</a></li>
        <li><a href="#">Cart(0)</a></li>
        <li><a href="#">Payment</a></li>
      </ul>
    </div>
    <div class="sitelogowrap">
      <a class="sitelogo">
      <img class="sitelogoimg" v-if="logo" src="static/logo.png"/>
      <img class="sitelogoimg" v-if="scrolllogo" src="static/logo_scroll.png"/>
    </a>
    </div>
  </div>
  <div class="scrolllogo" v-if="logo">
  <div class="title_liner">
    <div class="title_liner_left"></div>
      <div class="title_liner_right"></div>
  </div>
  </div>
  <div class="nav_bar">
    <div class="catnav">
      <ul class="catnav_list">
        <li><a href="#">Home</a></li>
        <li><a href="#">men</a></li>
        <li><a href="#">female</a></li>
        <li><a href="#">group buy</a></li>
        <li id="search_li">
          <form class="search_box"  v-bind:class="{searchon:ison}">
            <input   v-on:focus="searchon"  v-on:blur="searchon" class="search" type="text" placeholder="Search"/>
            <input   class="search_submit" type="submit" />
          </form>
        </li>
      </ul>
    </div>
  </div>
</div>
  <div style="height:3000px;">
  </div>
</div>
</template>


<script>
export default {
  name: 'pageHeader',
  data: function () {
    return {
      msg: 'Welcome to Your Vue.js App',
      ison: false,
      logo: true,
      scrolllogo: false,
      headfix: false
    }
  },
  methods: {
    searchon: function (event) {
      this.ison = !this.ison
    }
  },
  mounted: function () {
    var that = this
    window.onscroll = function (e) {
      var scrolltop = document.documentElement.scrollTop || document.body.scrollTop
      if (scrolltop > 50) {
        that.logo = false
        that.headfix = true
        that.scrolllogo = true
      } else {
        that.logo = true
        that.scrolllogo = false
      }
    }
  }

}
</script>


<style scoped>
a{
  text-decoration: none;
  color:white;
}
*{
  margin:0;
  padding: 0;
}
.headfixed{
  position: fixed;
}
.container{
  height:50px;
  width: 100%;
  background: #262626;
  position: fixed;
}
.nav{
  float:right;
}
.container_itemlist{
  list-style: none;
}
.container_itemlist li{
  float: left;
  padding: 8px 0;
  box-sizing: border-box;

}
.container_itemlist li a{
padding: 10px;
font-size: 12px;
line-height: 1;
display: block;
    box-sizing: border-box;
}
.catnav_list{
  list-style: none;
  display: inline-block;
position: relative;
left: 2.3%;
}
.catnav_list li{
  display: inline-block;
  padding: 0 9px 0 0;

}
.catnav_list li a{
   font-size: 16px;
   display: inline-block;
   padding: 0px 10px;
}
.nav_bar{
  height:48px;
  background-color: #262626;
  line-height: 48px;
}
.catnav{
  margin: 0 auto;
text-align: center;
max-height: 100%;
max-width: 768px;
}
.search{
  border:1px solid white;
  background: #262626;
  outline: 0;
  border-radius:2px;
  padding: 5px 0px ;
  width:100%;
  padding-left: 5px;
    box-sizing: border-box;
}
.search:focus{
box-shadow: none;
color:white;

}
.search_submit{
  border: none;
background: #262626;
outline: 0;
position: absolute;
right:1px;
top:15px;
color: white;
}
.sitelogo{
 margin-left: -50%;
}
.scrolllogo{
  height: 56px;
  background:  #262626;
  padding-top: 50px;
}
.sitelogowrap{
  position: relative;
  width:144px;
  top:23px;
  left:50%;
}
.search_box{
  position: relative;
  width:60%;
  transition: width 0.5s;
}
 .search_box.searchon{
   position: relative;
   width:100%;
   transition: width 0.5s;
 }
#search_li{
  width:200px;
  position:relative;
}
.title_liner{
  word-spacing:-5px;
}
.title_liner_left{
  display: inline-block;
  position: relative;
  width: 50%;
  left: -100px;
  background-color: white;
  height:1px;
}
.title_liner_right{
  display: inline-block;
  position: relative;
  width: 50%;
  right:-100px;
  background-color: white;
  height:1px;

}
@media screen and (max-width: 767px){
  .catnav_list{
    list-style: none;
    display: block;
  position: relative;
  width:100%;
  }
  .catnav_list li{
    display: block;
    padding:0;

  }
  .catnav{
    text-align: left;
  }
  .nav_bar{
    height:auto;
  }
}
</style>
