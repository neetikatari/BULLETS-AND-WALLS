# p5.play-boilerplate
Boiler plate for p5.play


var thickness, wall
var speed,weight,bullet

function setup() {
  createCanvas(1600,400);
  speed = random (223,321)
  weight = random (30,52)
  thickness =random(22,83);

  bullet = createSprite(50,200,50,20);
  bullet.velocityX = speed
  bullet.shapeColor="white"

  wall = createSprite(1200,200,thickness,height/2)
  wall.shapeColor= color(80,80,80);
 

}

function draw() {
    background(0); 
    
    text ("speed : " +speed,200,50)
    text("weight : " +weight, 200,70)
   

    if(wall.x - bullet.x < bullet.width/2 +wall.width/2){
      bullet.velocityX=0;
      var damage = (0.5 * weight * speed * speed) / (thickness*thickness*thickness);
      text("damage : "+damage,200,110)
      if(damage >10){
        wall.shapeColor="green"
        textSize(28)
        text("wall is not effective against bullet ", 200,200)
      }

      else{
        wall.shapeColor="red"
        textSize(28)
        text("wall is effective against bullet ", 200,200)
      }
    }

    drawSprites();
}