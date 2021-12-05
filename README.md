
Thanks for visiting my github profile. Have a great day ahead!
  
<h2 align="center"> ✨ About Me ✨</h2>
  
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
