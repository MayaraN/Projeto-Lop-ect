# Projeto-Lop-ect
/* 
   Equipe: 
      Mayara Felipe de Nogueira I - Subturma C (Líder) 
      Daiane Fagundes Pinheiro da Silva II - Subturma C
      Etapa 3
*/

var xo=100; 
var yo=100; 
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

ellipse(xo,yo,80,80); 
  xo = xo+6;
  if (xo > 400){
    xo = -random (1000);
    console.log(xo);
  }
fill(30,200,500); 
rect(200,269,80,80); 
stroke(0,0,10);
}
