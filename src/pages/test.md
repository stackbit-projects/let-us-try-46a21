---
title: How to make a website with Stackbit
subtitle: It is awesome
image_alt: YEA
seo:
  title: 'How to make a website with Stackbit'
  description: 'How to make a website with Stackbit'
  robots: []
  extra: []
  type: stackbit_page_meta
template: page
---
## Lorem ipsum

This is super cool

- Lorem ipsum
- dolor sit amet


let distance = 169.87;
let colors = ['#ffe700', '#ffb937', '#FFA500', '#ff5033', '#e32f11','#a31c04', '#e22467','#861576', '#251586'];
let numFaces = 9;

function createFaces() {
  
  for (let i = 1; i < numFaces + 1; i++) {
    
    let pathEl = document.createElementNS("http://www.w3.org/2000/svg", "path");
    
    pathEl.setAttribute("id", 'face_' + i);  
    pathEl.setAttribute('d','M' + distance + '26.318006 c 29.3,24.77 29.07,40.97 19.24,85.749994 -0.53,10.83 14.07,-3.14 18.13,7.25 10.24,9.01 4.88,9.33 5,16.38 5.9,9.29 -5.01,16.41 -1.87,20.75 -0.93,13.28 -8.42,20.29 -19.5,33 -8.41,14.51 -38.2,-1.28 -38.38,-1.25 -2.68,1.13 9.3,18.36 21.62,28.88 20.4,13.44 39.98,56.17 48.13,79.37 0,0 -221.25000843,-0.37 -221.25000843,-0.87 17.12000043,-31.59 35.20000043,-79.82 75.00000043,-69.63 2.4,-24.69 0.51,-35.26 -26.62,-60 -5.88,-3.37 -18,-5.75 -29.13,-5.75 -31.090001,-3.55 -8.73,-21.27 -15.2500004,-29.25 -2,-5.25 -0.88,-8.25 3,-8.25 3.7500004,0 3.8800004,-1.5 0.25,-3.13 -8.98000023,-4.56 0.76,-11.59 2.0000004,-14.87 0,-0.62 -2.7500004,-2.38 -5.5000004,-5.499996 -16.9500006,-22.589998 21.9600004,-9.39 25.8700004,-39.999998 0.63,-6.13 2,-9 9.88,-20.88 38.52,-64.8 117.690008,-22.07 129.380008,-12' + 'z' + distance);
    pathEl.style.fill = 'none';
    pathEl.style.stroke = colors[i-1];
    pathEl.style.strokeWidth = '1.2';
    pathEl.style.opacity = 1;  
    document.querySelector('svg').appendChild(pathEl);
    distance += 20;
    
  }
  
}

function outlinesTimeline() {
  
  let outlinesTL = new TimelineMax();
 
  for (let i = 1; i < numFaces + 1; i++) {
  
    outlinesTL.from('#face_'+i, 0.3, 
                    {css: {autoAlpha: 0}, yoyo:true, ease: Power0.easeInOut},
                    '-=0.2')
  }
  
  outlinesTL
    .fromTo('#sun', 1.2, {css: {autoAlpha: 1}}, {css: {autoAlpha:0.4}, 
                                          yoyo:true, ease: Power1.easeInOut},'-=1.5')
    .fromTo('#sun',1.2, {attr: {fill:'#251586'}}, {attr: {fill:'red'}, 
                                          yoyo:true, ease: Power1.easeInOut},'-=1')
    .fromTo('#sun',1.4,{css:{scale:0.6}},{scale:1, 
                                          yoyo:true, ease: Power1.easeInOut},'-=1.5')
    .fromTo('#pattern_7',1.2,{attr:{fill:'none'}},{attr:{fill:'red'}, 
                                          yoyo:true, ease: Power1.easeInOut},'-=1.5');

  return outlinesTL;
  
}

function fillColorTimeline() {
  
  let fillTL = new TimelineMax();
  
  for (let i = 9; i > 0; i--) {
  
  fillTL
    .fromTo('#face_'+i,0.07,{css:{fill:'none'}},{css:{fill:colors[i-1]}, yoyo:true, ease: Power1.easeInOut})
    .fromTo('#face_'+i,0.07,{css:{autoAlpha:'0.3'}},{css:{autoAlpha:'0.5'}, yoyo:true, ease: Power0.easeInOut},'-=0.02')
    
  }
  
  fillTL
    .fromTo('#sun',1.2,{attr:{fill:'red'}},{attr:{fill:'#251586'}, yoyo:true, ease: Power1.easeInOut},'-=1')
    .fromTo('#sun',1.2,{css:{autoAlpha:0.6}},{css:{autoAlpha:0.9}, yoyo:true, ease: Power1.easeInOut},'-=1.5')

  return fillTL;
  
}

function squeezeTimeline() {

  let squeezeTL = new TimelineMax();

  for (let i = 8; i > 0; i--) {
  
   squeezeTL
      .fromTo('#face_'+i,0.4,{css:{autoAlpha:1}},{css:{autoAlpha:0},ease: Power1.easeInOut},'-=0.2')
    
  }

  squeezeTL
    .fromTo('#face_9',1,{x:0},{x:-150,ease: Power1.easeInOut},'-=0.2')
    .fromTo('#face_9',1,{css:{autoAlpha:'0.5'}},{css:{autoAlpha:'1'},ease: Power1.easeInOut},'-=1')
  
  return squeezeTL;

}

function animateFaces() {
  
  let masterTL = new TimelineMax();

  masterTL
    .add(outlinesTimeline())
    .add(fillColorTimeline())
    .add(squeezeTimeline())
  ;
  
}

createFaces();
animateFaces();


