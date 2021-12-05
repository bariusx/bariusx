const path = require("path");
const fetch = require("node-fetch");
const fs = require("fs");

let stars = 0,
  page = 1;

const CountStars = async () => {
  let StarsData = await fetch(
    `https://api.github.com/users/barius13/starred?per_page=100&page=${page}`
  ).then((res) => res.json());
  stars += StarsData.length;
  page++;
  if (StarsData.length === 100) CountStars();
  else WriteReadMe();
};

const WriteReadMe = async () => {
  //Get ReadMe path
  const ReadMe = path.join(__dirname, "..", "README.md");
  const date = new Date();

  //Fetching Info From Github API
  let UserData = await fetch("https://api.github.com/users/barius13").then(
    (res) => res.json()
  );

  //Creating the text what we gonna save on ReadMe file
  const text = `##I am kms
  
Thanks for visiting my github profile. Have a great day ahead!
  
<h2 align="center"> ✨ About Me ✨</h2>
\`\`\`js
const Sudhan = {
    FavouriteLanguage: "Javascript/Typescript",
    OpenedIssues: {{ ISSUES }},
    OpenedPullRequests: {{ PULL_REQUESTS }},
    TotalCommits: {{ COMMITS }},
    Stars: ${stars},
    Repositories: {
       Created: {{ REPOSITORIES }},
       Contributed: {{ REPOSITORIES_CONTRIBUTED_TO }}
    },
}; //Balls
\`\`\`
  
<h2 align="center"> 🚀 My Stats 🚀</h2>
<p align="center">
<img src="https://github-readme-streak-stats.herokuapp.com/?user=barius13&theme=tokyonight">
</p>
<details>
  <summary>
      Even more stats
  </summary>
  <p align="center">
    <img src="https://github-profile-trophy.vercel.app/?username=barius13&theme=dracula">
    <img src="https://github-readme-stats.vercel.app/api?username=barius13&theme=tokyonight">
  </p>
</details>
  
<!-- Last updated on ${date.toString()} ;-;-->
<i>Last updated on ${date.getDate()}${
    date.getDate() === 1
      ? "st"
      : date.getDate() === 2
      ? "nd"
      : date.getDate() === 3
      ? "rd"
      : "th"
  } ${
    [
      "January",
      "February",
      "March",
      "April",
      "May",
      "June",
      "July",
      "August",
      "September",
      "October",
      "November",
      "December",
    ][date.getMonth()]
  } ${date.getFullYear()} using magic</i> ✨`;

  //Saving on readme.md
  fs.writeFileSync(ReadMe, text);
};

(() => {
    CountStars();
})()
