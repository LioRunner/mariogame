var rocketID = 0;
var rocketRemoveCount = 0;
$(function() {
    var interval = setInterval(createRokcet, 1000);
    var interval2 = setInterval(checkGame, 100);
    var count = 0;
    backStart();
    $("#jumpButton").on("click",function(){
        $("#mario").animate({
                top: '200px'
            }, 300, function() {
                $(this).animate( {
                    top: '375px'
            }, 300 );
        });
    });    
    $("#stopButton").on("click", function() { clearInterval(interval); clearInterval(interval2);  }); 
});
function checkGame() {
    for(index = rocketRemoveCount; index < rocketID; index++) {
        console.log("check");
        var x = parseInt($("#rocket" + index).css("left").replace("px", ""));
        if(x <= -100) {
            console.log("rocket" + index + " removed");
            $("#rocket" + index).remove();
            rocketRemoveCount++;
        }
        if( rectinrect(마리오값, rocket+index)  == true ) {
            
        }
    }
}
function createRokcet() {
    $("#outterBox").append("<div id='rocket" + rocketID + "' class='rocketStyle'>" +
                            "<img src='a.png' width='100%' height='100%'>" +
                            "</div>");
    $("#rocket" + rocketID).animate({
        left: '-100px'
    },3000);
    rocketID++;
}

function backStart() {
    $("#background1").css("left", "0px");
    $("#background1").animate({
        left: '-1000px'
    },5000, "linear", backStart);
}
