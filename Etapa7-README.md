# Projeto-Lop-ect
/* 
   Equipe: 
      Mayara Felipe de Nogueira - Subturma C (Líder) 
      Daiane Fagundes Pinheiro da Silva - Subturma C
      Etapa 7
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
var vxo=[];
var vyo=[];
var qtObjetos=4;
var vVel=[];
var barreiraDePontos = 100;
var nivel = 0;


let imgQuimico;
function preload() {
  imgQuimico = loadImage('john frink.png');
}

function setup() { 
  createCanvas(400, 400);
  for( var i=0; i<qtObjetos; i++){
    vxo[i]=random(0, 400);
    vyo[i]=-random(0, 400);
    vVel[i]=random(1, 8);
  }
}

function draw() {
  background(150,200,100); 
  fill(0, 102,153);
  textSize(18);
  text("Vidas: "+vidas, 10, 30);
  text("Pontos: "+pontos, 150, 30);
  text("Nível: "+dificuldade, 300, 30);
  //Incremento de pontos
  pontos = pontos  + 10;
  
  if( pontos > barreiraDePontos ){
    nivel++;
    barreiraDePontos =  barreiraDePontos + 100;
  }
  
  if (keyIsDown(LEFT_ARROW)){
    x=x-7;
}

if (keyIsDown(RIGHT_ARROW)){
  x=x+7; 
}

if (keyIsDown(UP_ARROW)){ 
  y=y-7;
}

if (keyIsDown(DOWN_ARROW)){
  y=y+7;
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
  
 for(var i=0; i<qtObjetos; i++){
   vyo[i] = vyo[i] + vVel[i];
   rect(vxo[i],vyo[i],50, 50);
   if(vyo[i] > 400){
     vyo[i] = -random(100, 200);
   }
   if (dist(x, y, vxo[i], vyo[i]) < raioP + raioO ){
      x=100; 
      y=360;
   }
 }
  stroke(0,0,10); 
}
