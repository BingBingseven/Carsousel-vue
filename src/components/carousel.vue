<template>
  <div>
        <ul id="slide_img">
          <li><a><img href="#" src="../assets/banner1.jpg"></a></li>
          <li><a><img href="#" src="../assets/banner2.jpg"></a></li>
          <li><a><img href="#" src="../assets/banner3.jpg"></a></li>
          <li><a><img href="#" src="../assets/banner4.jpg"></a></li>
          <li><a><img href="#" src="../assets/banner5.jpg"></a></li>
          <li><a><img href="#" src="../assets/banner1.jpg"></a></li>
        </ul>
        <ul id="index_list">
          <li class="hover">1</li>
          <li>2</li>
          <li>3</li>
          <li>4</li>
          <li>5</li>
        </ul>
  </div>
</template>

<script>
export default {
  name: 'carousel',
  mounted(){
    const WIDTH = 1280,
          WAIT = 2500,
          INTERVAL = 800; 
     let  canMove = true,
          timer = null,
          moved = 0;
          function move() {
    if (canMove) {
        timer = setTimeout(() => {
            moved++;
            $("#slide_img").animate({ left: -WIDTH * moved }, INTERVAL, () => {
                if (moved < 5) {
                    $("#index_list").children(`:eq(${moved})`).addClass("hover").siblings().removeClass("hover");
                } else{
                    moved = 0;
                    $("#slide_img").css("left", 0);
                    $("#index_list").children(":first").addClass("hover").siblings().removeClass("hover");
                }
                move();
            })
        }, WAIT);
    }
  };
  move();
  $("#app").hover(
    () => {
        clearTimeout(timer);
        canMove = false;
        timer = null;
    },
    () => {
        canMove = true;
        move();
    }
  );
  $("#index_list").on("mouseover", "li", e => {
    var $li = $(e.target);
    moved = $li.index();
    $("#slide_img").stop(true).animate({
        left: -WIDTH * moved
    }, INTERVAL);
    $li.addClass("hover").siblings().removeClass("hover");
  })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#slide_img {
    width:7680px;
    position: absolute;
    top: 0;
    left: 0;
}
#slide_img>li>a>img{
  width:1280px;
}

#slide_img>li {
    float: left;
}

#index_list {
    position: absolute;
    top: 90%;
    left: 45%;
}

#index_list>li {
    border: 1px solid #ddd;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    display: inline-block;
    margin-right: 10px;
    background: #eee;
    font-size:12px;
}

#index_list>li.hover {
    background: #78A000;
}
</style>
