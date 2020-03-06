# March-5th-Check-in
My Project so far

let video;
let poseNet;
let noseX = 0;
let noseY = 0;
let eyelX = 0;
let eyelY = 0;
let eye2X = 0;
let eye2Y = 0;
let ear1X = 0;
let ear1Y = 0;


 
function setup() {
  createCanvas(800, 800);
  video = createCapture(VIDEO);
  video.hide();
  poseNet = ml5.poseNet(video, modelReady);
  poseNet.on('pose', gotPoses);
}



function gotPoses(poses) {
  // console.log(poses);
  if (poses.length > 0) {
    let nX = poses[0].pose.keypoints[0].position.x;   //The different face points
    let nY = poses[0].pose.keypoints[0].position.y;
    let eX = poses[0].pose.keypoints[1].position.x;
    let eY = poses[0].pose.keypoints[1].position.y;
    let aX = poses[0].pose.keypoints[2].position.x;
    let aY = poses[0].pose.keypoints[2].position.y;
    let bX = poses[0].pose.keypoints[3].position.x;
    let bY = poses[0].pose.keypoints[3].position.y;
    noseX = lerp(noseX, nX, 0.5);
    noseY = lerp(noseY, nY, 0.5);
    eyelX = lerp(eyelX, eX, 0.5);
    eyelY = lerp(eyelY, eY, 0.5);
    eye2X = lerp(eye2X, aX, 0.5);
    eye2Y = lerp(eye2Y, aY, 0.5);
    //ear1X = lerp(ear1X, bX, 0.5);
    //ear1Y = lerp(ear1Y, bY
  }
}



function modelReady() {
  console.log('model ready');
}

function draw() {
  //image(video, 0, 0);
 
  let d = dist(noseX, noseY, eyelX, eyelY, eye2X, eye2Y); // not using right now,but clown nose :0)



  fill(255, 0, 0);
  ellipse(noseX, noseY, 50);
  fill(0,0,255);
  ellipse(eyelX, eyelY, 25);
  fill(0,255,0);
  ellipse(eye2X, eye2Y, 25);
  fill(0,255,0);

