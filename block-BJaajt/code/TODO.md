# Github User Finder

Your app will do the following:

- A input box where you can type the username of any user in the world and press `enter`
- Your app internally will interact with `github` api at `https://api.github.com/user/{username}`
- Get the user data and display it on the page.
- Display the user information like profile picture, username, number of followers and following etc
- Display the first five following/followers user (show image, username)

- API: https://api.github.com/users/{username}
- Followers List: https://api.github.com/users/{username}/followers
- Following List: https://api.github.com/users/{username}/following

# Cat Image Website

Your app will do the following:

- Display an image of cat coming from thecatapi link given below.
- Add a button with the text `Get New Cat`
- When clicked it will display image of a new cat

- Cat Image API (https://api.thecatapi.com/v1/images/search?limit=1&size=full)
let img = document.querySelector("img")
let input = document.querySelector("input");
let name = document.querySelector("h1");
let p = document.querySelector("p");
let followers = document.querySelector(".followers");
let following = document.querySelector(".following");


function displayUi(data){
img.src = data.avatar_url
name.innerText = data.name
p.innerText = data.company
following.innerText = `following: ${data.following}`
followers.innerText = `followers: ${data.followers}`

}


function handleClick(event){
  if(event.keyCode ===13){
    let xhr = new XMLHttpRequest();
    xhr.open("GET",`https://api.github.com/users/${event.target.value}`)
    xhr.onload = function(){
      let data = JSON.parse(xhr.response)
      displayUi(data);
    }
    xhr.send();
  }

 
}


input.addEventListener("keyup",handleClick)



