# Projeto-Lop-ect
/* 
   Equipe: 
      Mayara Felipe de Nogueira - Subturma C (Líder) 
      Daiane Fagundes Pinheiro da Silva - Subturma C
      Etapa 9
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
var qtObjetos=4;
var vVel=[];
var barreiraDePontos = 100;
var tela = 1;
var tempo = 0;


var imgQuimico;
var imgInimgo;
var imgFundo;
function preload() {
  imgQuimico = loadImage('john frink.png');
  imgInimigo = loadImage('atomo2.jpg');
  imgFundo = loadImage('fundo.jpg');
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
    textSize(32);
    fill(135, 206, 235);
    text("Pressione Enter para começar ", 50, 160);
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
    //implementar a dinamica de mudança de nivel
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
    textSize(32);
    fill(135, 206, 235);
    text("Game Over", 50, 160);
  }
  
    
  
}
