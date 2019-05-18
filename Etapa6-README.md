# Projeto-Lop-ect
/* 
   Equipe: 
      Mayara Felipe de Nogueira - Subturma C (Líder) 
      Daiane Fagundes Pinheiro da Silva - Subturma C
      Etapa 6
*/

var x=100; 
var y=400;
var xo=200; 
var yo=20; 
var xd=0;
var yd=0;
var estadoDisparo = false;
var raioP=40;
var raioO=40;
var vidas=3;
var pontos=0;
var dificuldade=1;

let imgQuimico;
function preload() {
  imgQuimico = loadImage('simpsons 2 quimico.png');
}

function setup() {
  background(50);
  image(imgQuimico, 10, 10, 50, 50);
}

function setup() { 
  createCanvas(400, 400);
}

function draw() {
  background(150,200,100); 
  fill(0, 102,153);
  textSize(18);
  text("Vidas: "+vidas, 10, 30);
  text("Pontos: "+pontos, 150, 30);
  text("Nível: "+dificuldade, 300, 30);
  
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
 fill(30,200,500);
 //ellipse(x,y,2*raioP,2*raioP);
 imageMode(CENTER);
 image(imgQuimico, x, y, 100, 100);
  if ( xo > width ){
    xo = 0;
  }
  if (keyIsDown(CONTROL) && estadoDisparo==false){
    xd = x;
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
 rect(xo,yo,80, 80);
  if (dist(x, y, xo, yo) < raioP + raioO ){
      x=100; 
      y=360;
      }
  yo = yo+3;
  if (yo > 400){
    yo = -random (1000);
    console.log(yo);
  }
  stroke(0,0,10); 
}
