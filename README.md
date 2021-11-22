# car-game-
var car1 = {
  x : 100,
  y : 230
  
  
}
var line1 = {
  x :100,
  x2 :300

}
var trash1 = {
  x : 300,
  y : 140
}
var score = 0;
var speed = -5

function setup() {
  createCanvas(600, 400);
}

function draw() {
  background(0);
  car();
 //move ();
  bounse();
  respawn();
  road();
  move2()
  respawn2 ();
  trash();
 balls();
  stop();
  textSize(20)
  text(score,width-50,20);
  
  
 
  
   
}
function car(x,y){
   stroke(255);
  strokeWeight(4);
  noFill();
  fill(random(255),0,random(255));
  ellipse(car1.x,car1.y,30,30);
  ellipse(car1.x+50,car1.y,30,30);
  rect(car1.x-20,car1.y-60,90,40);
  
  
}
function move (){
  car1.x= car1.x + speed;
  
}
function bounse (){
//if ((cars.x +60) >width || (cars.x -20) < 0 ){
 // speed = speed * -1
//}
}
function respawn (){
  if((car1.x-20)>width){
    car1.x=0;
  }
}
function road(){
   line(0,70,width,70)
  line(0,250,width,250)
  line(line1.x,160,line1.x2,160)

  
}
function mousePressed(){
  if(mouseY<150){
    car1.y = 140
  }
  else{
    car1.y=230
  }
  
}

function move2(){
  line1.x = line1.x + speed
  line1.x2 = line1.x2 + speed
   trash1.x+=speed
  
}
function respawn2 (){
  if(line1.x<0 && line1.x2 < 0 ){
    line1.x=width
    line1.x2=width+200
  }
    
  }

function trash(x,y){
  ellipse(trash1.x,trash1.y,25,25)  
}
function stop(){
   if ((car1.x+80==trash1.x) && car1.y==trash1.y ){
     speed = 0
   }
}
function balls(){
  // fucking balls
 if((trash1.x<=0) && (trash1.y<=140) ){
    trash1.x = width
    trash1.y = 230
   score += 10;
   multiplier = Math.floor((score / 100))+1
  if(score%100 == 0  && score>0 ){
    speed = speed*multiplier;
  }
  }
  else if ((trash1.x<=0) &&(trash1.y== 230) ){
    trash1.x=width ;
    trash1.y= 140 ;
score += 10;
    multiplier = Math.floor((score / 100))+1
  if(score%100 == 0  && score>0 ){
    speed = speed*multiplier;
  }
  }
  
}
