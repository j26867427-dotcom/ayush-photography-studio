<!DOCTYPE html>
<html>
<head>
<title>Ayush Photography Studio</title>

<style>

body{
margin:0;
font-family:Arial;
background:url("https://images.unsplash.com/photo-1516035069371-29a1b244cc32");
background-size:cover;
color:white;
}

header{
background:rgba(0,0,0,0.8);
padding:15px;
text-align:center;
font-size:28px;
}

nav{
background:#000;
display:flex;
justify-content:center;
}

nav button{
background:none;
border:none;
color: gold;
padding:15px 20px;
font-size:16px;
cursor:pointer;
}

nav button:hover{
background:#ff9800;
}

.page{
display:none;
padding:20px;
}

.active{
display:block;
}

.gallery img{
width:200px;
margin:10px;
border-radius:10px;
}

video{
width:250px;
margin:10px;
border-radius:10px;
}

input,select,textarea,button{
padding:10px;
margin:5px;
width:90%;
max-width:400px;
}

button{
background:#ff9800;
border:none;
color:white;
cursor:pointer;
}

.frame{
border:2px solid white;
padding:10px;
margin:10px;
display:inline-block;
}

</style>

</head>

<body>

<header>
📸 Ayush Photography Studio
</header>

<nav>

<button onclick="showPage('home')">Home</button>
<button onclick="showPage('photo')">Photo Gallery</button>
<button onclick="showPage('video')">Video Gallery</button>
<button onclick="showPage('frame')">Frames</button>
<button onclick="showPage('price')">Price</button>
<button onclick="showPage('order')">Book Order</button>
<button onclick="showPage('feedback')">Feedback</button>

</nav>


<!-- HOME -->

<div id="home" class="page active">

<h2>Studio Profile</h2>

<p><b>Studio Name:</b> Ayush Photography Studio</p>

<p>
Wedding Shoot , 
Birthday Shoot ,
Reel Shoot ,
Album Design ,
Video Shoot and 
other shoot.
</p>

<h3>Follow Us</h3>

<p>Instagram: @ayushmaurya1212</p>
<p>YouTube: Ayush photography studio</p>

</div>


<!-- PHOTO GALLERY -->

<div id="photo" class="page">

<h2>Photo Gallery</h2>

<input type="file" accept="image/*" onchange="uploadPhoto(event)">

<div id="photoGallery" class="gallery"></div>

</div>


<!-- VIDEO GALLERY -->

<div id="video" class="page">

<h2>Video Gallery</h2>

<input type="file" accept="video/*" onchange="uploadVideo(event)">

<div id="videoGallery"></div>

</div>


<!-- FRAME -->

<div id="frame" class="page">

<h2>Photo Frames</h2>

<input type="file" accept="image/*" onchange="uploadFrame(event)">

<input type="text" id="frameSize" placeholder="Frame Size (12x18 etc)">

<input type="text" id="framePrice" placeholder="Price">

<button onclick="addFrame()">Add Frame</button>

<div id="frameGallery"></div>

</div>


<!-- PRICE -->

<div id="price" class="page">

<h2>Price List</h2>

<p>Wedding Shoot : ₹15000</p>
<p>Birthday Shoot : ₹5000</p>
<p>Reel Shoot : ₹2000</p>
<p>Passport Photo : ₹100</p>
<p>Video Shoot : ₹8000</p>

</div>


<!-- ORDER -->

<div id="order" class="page">

<h2>Book Order</h2>

<input type="text" id="name" placeholder="Customer Name">

<input type="text" id="phone" placeholder="Phone">

<select id="service">
<option>Wedding Shoot</option>
<option>Birthday Shoot</option>
<option>Video Shoot</option>
<option>Album Design</option>
</select>

<input type="date" id="date">

<button onclick="bookOrder()">Book</button>

<ul id="orders"></ul>

</div>


<!-- FEEDBACK -->

<div id="feedback" class="page">

<h2>Customer Feedback</h2>

<input type="text" id="customer" placeholder="Your Name">

<textarea id="message" placeholder="Write feedback"></textarea>

<button onclick="addFeedback()">Submit</button>

<ul id="feedbackList"></ul>

</div>



<script>

function showPage(page){

let pages=document.querySelectorAll(".page");

pages.forEach(p=>p.classList.remove("active"));

document.getElementById(page).classList.add("active");

}


function uploadPhoto(event){

let file=event.target.files[0];

let url=URL.createObjectURL(file);

let img=document.createElement("img");

img.src=url;

document.getElementById("photoGallery").appendChild(img);

}


function uploadVideo(event){

let file=event.target.files[0];

let url=URL.createObjectURL(file);

let video=document.createElement("video");

video.src=url;

video.controls=true;

document.getElementById("videoGallery").appendChild(video);

}


let frameImage="";

function uploadFrame(event){

let file=event.target.files[0];

frameImage=URL.createObjectURL(file);

}

function addFrame(){

let size=document.getElementById("frameSize").value;

let price=document.getElementById("framePrice").value;

let div=document.createElement("div");

div.className="frame";

div.innerHTML=`

<img src="${frameImage}" width="200"><br>
Size: ${size}<br>
Price: ₹${price}

`;

document.getElementById("frameGallery").appendChild(div);

}


function bookOrder(){

let name=document.getElementById("name").value;

let service=document.getElementById("service").value;

let date=document.getElementById("date").value;

let li=document.createElement("li");

li.innerText=name+" - "+service+" - "+date;

document.getElementById("orders").appendChild(li);

}


function addFeedback(){

let name=document.getElementById("customer").value;

let msg=document.getElementById("message").value;

let li=document.createElement("li");

li.innerText=name+" : "+msg;

document.getElementById("feedbackList").appendChild(li);

}

</script>

</body>
</html>
