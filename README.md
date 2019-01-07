# Tomagatchi
Homework project of Tomagatchi
class Tomagotchi {
    constructor(name) {
        this.name
        this.hunger = 0
        this.sleepy = 0
        this.boredom = 0
        this.age = 0
    }
    feed(){
    	this.hunger -= 1
    	$("#hungerVal").text(" " + this.hunger)
    	if (this.hunger <= 0) {
        	this.hunger = 0
        	$("#hungerVal").text(" " + this.hunger)
    	}
    }
}

let inGameTime = 2000
let tammy = new Tomagotchi("Tammy")
let feed = $("#feed")
let lights = $("#lightsOnOff")
let switchOF = $("#offOn")
let play = $("#play")
let feedVal = $("#feed")
let age = $("#age")

let domInput = function() {
	return $("#nameVal").val()
}

feed.click(tammy.feed)

lights.click(function () {
    if (switchOF.text() === "On") {
        switchOF.text("Off")
    } else {
        switchOF.text("On")
    }
})

play.click(function () {
    tammy.boredom -= 1
    $("#boredomVal").text(" " + tammy.boredom)
    if (tammy.boredom <= 0) {
        tammy.boredom = 0
        $("#boredomVal").text(" " + tammy.boredom)
    }
})

let insatiate = function () {
    setTimeout(function () {

        tammy.hunger += 1
        tammy.boredom += 1
        tammy.sleepy += 1
        $("#hungerVal").text(" " + tammy.hunger)
        $("#boredomVal").text(" " + tammy.boredom)
        $("#sleepyVal").text(" " + tammy.sleepy)

        if (tammy.hunger >= 10 || tammy.boredom >= 10 || tammy.sleepy >= 10) {
        	//show image of tammy dead
            $(".tammy").attr("src", "https://media.istockphoto.com/vectors/skull-and-crossbones-icon-on-white-background-vector-vector-id539681702?k=6&m=539681702&s=612x612&w=0&h=L-g4EAUBqvEWIoXrY-M10qsmCqKeC0wZcprX4pw9DK8=")
            tammy.hunger = 10
            tammy.boredom = 10
            tammy.sleepy = 10
        }
        else{
      	  insatiate()
    	}
    }, inGameTime);

        
}
insatiate()

let ageTammy = function () {
    setTimeout(function () {
        tammy.age += 1
        age.text(" " + tammy.age)
        ageTammy()
        if (tammy.age >= 10) {
            $(".tammy").attr("src", "https://d1u5p3l4wpay3k.cloudfront.net/bindingofisaacre_gamepedia/9/95/Boss_The_Gate.png?version=f92a360ed281e74f4a966b7a440ac1f3")
        }
    }, inGameTime);
}
ageTammy()

$("#lightsOnOff").click(function () {
    $(".blackedOut").removeClass("runAni")
    if (switchOF.text() === "Off") {
        $(".blackedOut").removeClass("runAni")
        console.log("SHOOT")
    } else {

        $(".blackedOut").addClass("runAni")
    }
})

$("button").click(function(){
	let petName = domInput()
	
	if(petName){
		$(".nameSection").append("Name: " + petName)
		this.remove()
		$("#nameVal").remove()
		console.log(petName)
	}
})
