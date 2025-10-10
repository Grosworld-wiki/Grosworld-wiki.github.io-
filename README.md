<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=1200, initial-scale=1, user-scalable=yes">
<title>Grosworld Wiki</title>
<style>
  body {
    margin: 0;
    font-family: Arial, sans-serif;
    background-color: #f4f4f4;
    overflow-x: auto;
  }

  .zoom-wrapper {
    transform: scale(1);
    transform-origin: top left;
    width: 1200px;
    margin: 0 auto;
  }

  header {
    width: 100%;
    background-color: #1a1a1a;
    color: #fff;
    padding: 15px 20px;
    box-sizing: border-box;
    position: sticky;
    top: 0;
    z-index: 100;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  header h1 {
    margin: 0;
    font-size: 28px;
    flex-shrink: 0;
  }

  .search-container {
    flex: 1;
    display: flex;
    justify-content: center;
  }

  header input {
    width: 400px;
    max-width: 80%;
    padding: 8px;
    border-radius: 5px;
    border: none;
    font-size: 16px;
  }

  .container {
    display: flex;
    padding: 20px;
    gap: 20px;
    box-sizing: border-box;
  }

  .sidebar {
    width: 220px;
    background-color: #fff;
    padding: 15px;
    box-shadow: 0 0 5px rgba(0,0,0,0.1);
    border-radius: 5px;
    height: calc(100vh - 80px);
    overflow-y: auto;
    flex-shrink: 0;
  }

  .sidebar h2 {
    margin-top: 0;
    font-size: 18px;
    border-bottom: 1px solid #ddd;
    padding-bottom: 5px;
  }

  .sidebar ul {
    list-style: none;
    padding: 0;
  }

  .sidebar li {
    margin: 10px 0;
    cursor: pointer;
    color: #333;
    transition: 0.2s;
    outline: none; /* mavi kutu kapalı */
  }

  .sidebar li:hover {
    color: #007bff;
  }

  .content {
    flex: 1;
    background-color: #fff;
    padding: 20px;
    box-shadow: 0 0 5px rgba(0,0,0,0.1);
    border-radius: 5px;
    height: calc(100vh - 80px);
    overflow-y: auto;
    scroll-behavior: smooth; /* smooth scroll */
  }

  .item-list {
    margin-top: 15px;
  }

  .item-list li {
    cursor: pointer;
    padding: 5px 0;
    transition: 0.2s;
    outline: none;
  }

  .item-list li:hover {
    color: #007bff;
  }

  .item-detail {
    margin-top: 30px;
    border-top: 1px solid #ccc;
    padding-top: 10px;
  }

  .item-detail h3 {
    margin-top: 20px;
  }
</style>
</head>
<body>

<div class="zoom-wrapper">

<header>
  <h1>Grosworld Wiki</h1>
  <div class="search-container">
    <input type="text" placeholder="Ara...">
  </div>
</header>

<div class="container">
  <div class="sidebar">
    <h2>Bölümler</h2>
    <ul>
      <li onclick="showSection('areas')">Areas</li>
      <li onclick="showSection('items')">Items & Equipment</li>
      <li onclick="showSection('monsters')">Monsters & Creatures</li>
      <li onclick="showSection('pets')">Pets</li>
      <li onclick="showSection('skills')">Skills</li>
    </ul>
  </div>

  <div class="content" id="content">
    <h2>Hoşgeldiniz!</h2>
    <p>Sol taraftan bir bölüm seçerek ilgili sayfalara ulaşabilirsiniz.</p>
  </div>
</div>

</div> <!-- zoom-wrapper -->

<script>
  const sectionData = {
    areas: ["Forest of Beginnings", "Desert of Despair", "Caves of Chaos"],
    items: ["Sword of Valor", "Shield of Light", "Potion of Healing"],
    monsters: ["Goblin", "Dragon", "Undead Knight"],
    pets: ["Mini Dragon", "Wolf Pup", "Magic Cat"],
    skills: ["Mining", "Fishing", "Swordsmanship"]
  };

  const itemDetails = {
    "Forest of Beginnings": "Forest of Beginnings hakkında detaylı bilgiler.",
    "Desert of Despair": "Desert of Despair hakkında detaylı bilgiler.",
    "Caves of Chaos": "Caves of Chaos hakkında detaylı bilgiler.",
    "Sword of Valor": "Sword of Valor güçlü bir silah.",
    "Shield of Light": "Shield of Light sağlam bir kalkan.",
    "Potion of Healing": "Potion of Healing sağlık yeniler.",
    "Goblin": "Goblin küçük ve tehlikeli bir canavar.",
    "Dragon": "Dragon güçlü ve ateş solur.",
    "Undead Knight": "Undead Knight zorlu bir düşmandır.",
    "Mini Dragon": "Mini Dragon küçük ama güçlü bir evcil hayvan.",
    "Wolf Pup": "Wolf Pup sadık bir evcil hayvandır.",
    "Magic Cat": "Magic Cat büyülü yeteneklere sahip.",
    "Mining": "Mining yeteneği maden kazmayı sağlar.",
    "Fishing": "Fishing yeteneği balık tutmayı sağlar.",
    "Swordsmanship": "Swordsmanship kılıç kullanma yeteneğidir."
  };

  function showSection(section){
    const contentDiv = document.getElementById("content");
    const items = sectionData[section];
    let html = `<h2>${capitalize(section)}</h2><ul class="item-list">`;
    items.forEach(item => {
      html += `<li onclick="scrollToItem('${item}')">${item}</li>`;
    });
    html += `</ul><div class="item-detail" id="item-detail">`;

    // Tüm itemlerin detaylarını göster
    items.forEach(item => {
      html += `<h3 id="${item.replace(/\s/g,'-')}">${item}</h3><p>${itemDetails[item]}</p>`;
    });
    html += `</div>`;

    contentDiv.innerHTML = html;
  }

  function scrollToItem(item){
    const el = document.getElementById(item.replace(/\s/g,'-'));
    if(el){
      el.scrollIntoView({behavior: "smooth", block: "start"});
    }
  }

  function capitalize(str){
    return str.charAt(0).toUpperCase() + str.slice(1).replace(/_/g, ' ');
  }
</script>

</body>
</html>
