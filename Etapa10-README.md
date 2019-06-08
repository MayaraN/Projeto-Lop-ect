# Projeto-Lop-ect
/* 
   Equipe: 
      Mayara Felipe de Nogueira - Subturma C (Líder) 
      Daiane Fagundes Pinheiro da Silva - Subturma C
      Etapa 10
*/

var x=250; 
var y=455;
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
var qtObjetos=6;
var vVel=[];
var barreiraDePontos = 100;
var tela = 1;
var tempo = 0;
var paraFrames = 0;
var contFrames = 0;
var imgQuimico = [];
var anima;


var imgQuimico;
var imgInimgo;
var imgFundo;
var imgFundo1;

function preload() {
  for (i=0; i<2; i++){ 
  imgQuimico[i] = loadImage('johnFrink'+i+'.png');
  }
  imgInimigo = loadImage('tubo5.png');
  imgFundo = loadImage('fundo.jpg');
  imgFundo1 = loadImage('FUNDO ADAPTADO.png');
}



function setup() { 
  createCanvas(500, 500);
  for( var i=0; i<qtObjetos; i++){
    vxo[i]=random(0, 470);
    vyo[i]=-random(0, 500);
    vVel[i]=random(1, 4);
  }
}

function draw() {
 
  
  if ( tela == 1 ){
    background(2);
    image(imgFundo1, -15, -8);
    textSize(40);
    fill(135, 206, 235);
    text("Pressione Enter", 190, 120);
    if(keyIsDown(ENTER)) {
      tela = 2;
    }
  }
  if ( tela == 2 ){
  background(2);
  image(imgFundo,250,270);
  fill(255, 204, 0);
  textSize(18);
  text("Vidas: "+vidas, 40, 30);
  text("Pontos: "+pontos, 200, 30);
  text("Nível: "+dificuldade, 390, 30);
    
   if( pontos > barreiraDePontos ){
    dificuldade++;
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
  anima = imgQuimico[contFrames];
 fill(30,200,500);
 //ellipse(x,y,2*raioP,2*raioP);
 imageMode(CENTER);
 image(anima, x, y, 100, 100);
    paraFrames++;
    if( paraFrames > 20 ){
      contFrames++;
      paraFrames = 0;
    }
    if ( contFrames > 1 ){
      contFrames = 0;
    }

  if ( x > width ){
    x = x-50;
  }
  if (x < 0 ){
    x = x+50;
  }
  if ( y > 480 ){
    y = y - 50;
  }
  if ( y < 0 ){
    y = y + 50;
  }
  if (keyIsDown(CONTROL) && estadoDisparo==false){
    xd = x;
    yd = y;
    estadoDisparo = true;
  }
  if ( estadoDisparo==true){
    ellipse(xd, yd, 10, 10)
    yd = yd-10;
    if( yd<0){
      estadoDisparo = false;
    }
  }
 fill(30,200,500); 
  
 for(var i=0; i<qtObjetos; i++){
   vyo[i] = vyo[i] + vVel[i];
   //rect(vxo[i],vyo[i],50, 50);
   image(imgInimigo,vxo[i],vyo[i], 50, 50);
   if(vyo[i] > 500){
     vyo[i] = -random(100, 200);
   }
   if (dist(x, y, vxo[i], vyo[i]) < 25 + 25 ){
      x=100; 
      y=360;
      vidas = vidas - 1;
     vxo[i] = random(0,400);
      vyo[i] = - random(0,400);
   }
   if(dist (xd, yd, vxo[i], vyo[i]) < 25 + 25){
      vxo[i] = random(0,400);
      vyo[i] = - random(0,400);
      estadoDisparo=false;
     pontos=pontos+10;
    }
 }
    if( vidas===0){
      tela=3;
    }
 
}

  if ( tela == 3 ){
    background(2);
    image(imgFundo1, 245, 250);
    textSize(40);
    fill(135, 206, 235);
    text("Game Over!", 220, 120);
  }
  
    
  
}
