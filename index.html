<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no">
<title>JEERACE 3D</title>

<style>
*{box-sizing:border-box}
body{
  margin:0;
  overflow:hidden;
  background:#111;
  font-family:Arial,sans-serif;
  touch-action:none;
}

#game{
  position:fixed;
  inset:0;
}

#menu{
  position:fixed;
  inset:0;
  z-index:10;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  background:linear-gradient(#07121dcc,#000);
  color:white;
}

#menu h1{
  font-size:55px;
  margin:0 0 10px;
  letter-spacing:5px;
}

#menu p{
  opacity:.8;
  margin-bottom:30px;
}

button{
  border:0;
  border-radius:15px;
  padding:15px 35px;
  font-size:20px;
  font-weight:bold;
  cursor:pointer;
}

#play{
  background:#fff;
  color:#111;
}

#hud{
  position:fixed;
  top:15px;
  left:15px;
  z-index:5;
  color:white;
  background:#0008;
  padding:12px 16px;
  border-radius:12px;
  font-size:17px;
  display:none;
}

#controls{
  position:fixed;
  bottom:25px;
  left:0;
  right:0;
  z-index:5;
  display:none;
  justify-content:space-between;
  padding:0 25px;
}

.controlGroup{
  display:flex;
  gap:15px;
}

.ctrl{
  width:70px;
  height:70px;
  border-radius:50%;
  border:2px solid #ffffff66;
  background:#0009;
  color:white;
  font-size:28px;
  user-select:none;
  -webkit-user-select:none;
}

.ctrl:active{
  background:#fff5;
}

#hint{
  position:fixed;
  bottom:15px;
  left:50%;
  transform:translateX(-50%);
  color:white;
  background:#0008;
  padding:7px 12px;
  border-radius:8px;
  font-size:13px;
  z-index:5;
}
</style>
</head>

<body>

<div id="game"></div>

<div id="menu">
  <h1>JEERACE</h1>
  <p>3D JEEP DRIVING</p>
  <button id="play">PLAY</button>
</div>

<div id="hud">
  SPEED: <span id="speed">0</span> km/h<br>
  DISTANCE: <span id="distance">0</span> m
</div>

<div id="hint">
  PC: W A S D / Arrow Keys &nbsp; • &nbsp; Mobile: Touch Controls
</div>

<div id="controls">

  <div class="controlGroup">
    <button class="ctrl" id="left">◀</button>
    <button class="ctrl" id="right">▶</button>
  </div>

  <div class="controlGroup">
    <button class="ctrl" id="brake">▼</button>
    <button class="ctrl" id="gas">▲</button>
  </div>

</div>

<script type="module">

import * as THREE from
"https://cdn.jsdelivr.net/npm/three@0.180.0/build/three.module.js";

let scene, camera, renderer;
let jeep;
let speed = 0;
let distance = 0;
let started = false;

const keys = {
  forward:false,
  backward:false,
  left:false,
  right:false
};

/* ---------------- SCENE ---------------- */

scene = new THREE.Scene();
scene.background = new THREE.Color(0x87ceeb);
scene.fog = new THREE.Fog(0x87ceeb,80,300);

camera = new THREE.PerspectiveCamera(
  65,
  innerWidth/innerHeight,
  0.1,
  500
);

camera.position.set(0,5,10);

renderer = new THREE.WebGLRenderer({
  antialias:true
});

renderer.setSize(innerWidth,innerHeight);
renderer.setPixelRatio(Math.min(devicePixelRatio,2));
renderer.shadowMap.enabled=true;

document.getElementById("game").appendChild(renderer.domElement);

/* LIGHT */

const sun = new THREE.DirectionalLight(0xffffff,2);
sun.position.set(30,60,20);
sun.castShadow=true;
scene.add(sun);

scene.add(new THREE.HemisphereLight(
  0xffffff,
  0x557755,
  1.2
));

/* GROUND */

const ground = new THREE.Mesh(
  new THREE.PlaneGeometry(500,500),
  new THREE.MeshStandardMaterial({
    color:0x3f7f3f
  })
);

ground.rotation.x=-Math.PI/2;
ground.receiveShadow=true;
scene.add(ground);

/* ROAD */

const road = new THREE.Mesh(
  new THREE.PlaneGeometry(18,500),
  new THREE.MeshStandardMaterial({
    color:0x303030
  })
);

road.rotation.x=-Math.PI/2;
road.position.y=.02;
scene.add(road);

/* ROAD LINES */

for(let z=-240;z<250;z+=12){

  const line = new THREE.Mesh(
    new THREE.BoxGeometry(.3,.03,6),
    new THREE.MeshStandardMaterial({
      color:0xffffff
    })
  );

  line.position.set(0,.06,z);
  scene.add(line);
}

/* ---------------- TREES ---------------- */

function makeTree(x,z){

  const trunk = new THREE.Mesh(
    new THREE.CylinderGeometry(.35,.5,3,8),
    new THREE.MeshStandardMaterial({
      color:0x654321
    })
  );

  trunk.position.set(x,1.5,z);
  scene.add(trunk);

  const leaves = new THREE.Mesh(
    new THREE.SphereGeometry(2.2,10,8),
    new THREE.MeshStandardMaterial({
      color:0x176b25
    })
  );

  leaves.position.set(x,4,z);
  leaves.castShadow=true;
  scene.add(leaves);
}

for(let z=-230;z<240;z+=18){

  makeTree(-15,z);
  makeTree(15,z+7);
}

/* ---------------- JEEP ---------------- */

function createJeep(){

  const group = new THREE.Group();

  /* BODY */

  const body = new THREE.Mesh(
    new THREE.BoxGeometry(3.2,1.1,5),
    new THREE.MeshStandardMaterial({
      color:0xd18b18
    })
  );

  body.position.y=1.25;
  body.castShadow=true;
  group.add(body);

  /* CABIN */

  const cabin = new THREE.Mesh(
    new THREE.BoxGeometry(2.7,1.3,2.5),
    new THREE.MeshStandardMaterial({
      color:0x222222
    })
  );

  cabin.position.set(0,2.25,.2);
  cabin.castShadow=true;
  group.add(cabin);

  /* WINDOWS */

  const windowMat = new THREE.MeshStandardMaterial({
    color:0x75b9d6,
    metalness:.2,
    roughness:.2
  });

  const frontWindow = new THREE.Mesh(
    new THREE.BoxGeometry(2.3,.7,.08),
    windowMat
  );

  frontWindow.position.set(0,2.35,-1.1);
  group.add(frontWindow);

  /* WHEELS */

  const wheelMat = new THREE.MeshStandardMaterial({
    color:0x111111
  });

  const wheelPositions=[
    [-1.65,.75,-1.6],
    [1.65,.75,-1.6],
    [-1.65,.75,1.6],
    [1.65,.75,1.6]
  ];

  wheelPositions.forEach(p=>{

    const wheel = new THREE.Mesh(
      new THREE.CylinderGeometry(.65,.65,.45,16),
      wheelMat
    );

    wheel.rotation.z=Math.PI/2;
    wheel.position.set(...p);
    wheel.castShadow=true;

    group.add(wheel);
  });

  /* HEADLIGHTS */

  const lightMat = new THREE.MeshStandardMaterial({
    color:0xffffaa,
    emissive:0xffff66,
    emissiveIntensity:1
  });

  [-1,1].forEach(x=>{

    const light = new THREE.Mesh(
      new THREE.SphereGeometry(.25,10,10),
      lightMat
    );

    light.position.set(x*.9,1.35,-2.55);
    group.add(light);
  });

  group.position.set(0,0,30);

  scene.add(group);

  return group;
}

jeep=createJeep();

/* ---------------- CONTROLS ---------------- */

window.addEventListener("keydown",e=>{

  if(e.key==="w" || e.key==="ArrowUp")
    keys.forward=true;

  if(e.key==="s" || e.key==="ArrowDown")
    keys.backward=true;

  if(e.key==="a" || e.key==="ArrowLeft")
    keys.left=true;

  if(e.key==="d" || e.key==="ArrowRight")
    keys.right=true;
});

window.addEventListener("keyup",e=>{

  if(e.key==="w" || e.key==="ArrowUp")
    keys.forward=false;

  if(e.key==="s" || e.key==="ArrowDown")
    keys.backward=false;

  if(e.key==="a" || e.key==="ArrowLeft")
    keys.left=false;

  if(e.key==="d" || e.key==="ArrowRight")
    keys.right=false;
});

/* MOBILE */

function touchButton(id,key){

  const b=document.getElementById(id);

  b.addEventListener("pointerdown",e=>{
    e.preventDefault();
    keys[key]=true;
  });

  b.addEventListener("pointerup",e=>{
    e.preventDefault();
    keys[key]=false;
  });

  b.addEventListener("pointercancel",()=>{
    keys[key]=false;
  });

  b.addEventListener("pointerleave",()=>{
    keys[key]=false;
  });
}

touchButton("gas","forward");
touchButton("brake","backward");
touchButton("left","left");
touchButton("right","right");

/* ---------------- GAME ---------------- */

function update(){

  if(!started) return;

  /* ACCELERATION */

  if(keys.forward){
    speed += .012;
  }else if(keys.backward){
    speed -= .018;
  }else{
    speed *= .985;
  }

  speed=Math.max(-.35,Math.min(speed,.65));

  /* STEERING */

  if(Math.abs(speed)>.01){

    if(keys.left){
      jeep.rotation.y += .025 * Math.sign(speed);
    }

    if(keys.right){
      jeep.rotation.y -= .025 * Math.sign(speed);
    }
  }

  /* MOVE */

  jeep.translateZ(speed);

  distance += Math.abs(speed);

  /* KEEP ROAD AREA */

  jeep.position.x=Math.max(-6,Math.min(6,jeep.position.x));

  /* CAMERA */

  const behind = new THREE.Vector3(
    0,
    4.8,
    9
  );

  behind.applyQuaternion(jeep.quaternion);
  behind.add(jeep.position);

  camera.position.lerp(behind,.08);

  const lookAt = jeep.position.clone();
  lookAt.y += 1.3;

  camera.lookAt(lookAt);

  /* HUD */

  document.getElementById("speed").textContent =
    Math.round(Math.abs(speed)*120);

  document.getElementById("distance").textContent =
    Math.round(distance);
}

/* ---------------- LOOP ---------------- */

function animate(){

  requestAnimationFrame(animate);

  update();

  renderer.render(scene,camera);
}

animate();

/* PLAY */

document.getElementById("play").onclick=()=>{

  started=true;

  document.getElementById("menu").style.display="none";
  document.getElementById("hud").style.display="block";
  document.getElementById("controls").
