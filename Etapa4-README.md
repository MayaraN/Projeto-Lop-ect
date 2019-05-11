# Projeto-Lop-ect
/* 
   Equipe: 
      Mayara Felipe de Nogueira I - Subturma C (Líder) 
      Daiane Fagundes Pinheiro da Silva II - Subturma C
      Etapa 4
*/

var x=100; 
var y=400;
var xo = 200; 
var yo = 20; 
var xd=0;
var yd=0;
var estadoDisparo = false;
function setup() { 
  createCanvas(400, 400);
}

function draw() {
  background(150,200,100); 
  if (keyIsDown(LEFT_ARROW)){
    x=x-5;
}

if (keyIsDown(RIGHT_ARROW)){
  x=x+5; 
}

if (keyIsDown(UP_ARROW)){ 
  y=y-5;
}

if (keyIsDown(DOWN_ARROW)){
  y=y+5;
}

ellipse(x,y,80,80); 
  

  if ( xo > width ){
    xo = 0;
  }
  if (keyIsDown(CONTROL) && estadoDisparo==false){
    xd = x,
    yd = y;
    estadoDisparo = true;
  }
  if ( estadoDisparo==true){
  ellipse(xd, yd, 4, 4)
  yd = yd-10;
    if( yd<0){
      estadoDisparo = false;
    }
  }
  fill(30,200,500); 
  rect(xo,yo,80,80);
  yo = yo+3;
  if (yo > 400){
    yo = -random (1000);
    console.log(yo);
  }
  stroke(0,0,10);
}
