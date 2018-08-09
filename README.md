# Vainglory Base Stats v3.6.1.0
A JSON object master file, hard-coded from the game itself, for use in web-based applications that can parse JSON data. Updated for VainGlory patch 3.3!

______________________

## Table of Contents
-  [Getting Started](#getting-started)
-  [Top-Level Data Objects](#top-level-data-objects)
-  [Accessing the Data (as a JavaScript object)](#accessing-the-data-as-a-javascript-object)
-  [Accessing the Data (with an Asynchronous call)](#accessing-the-data-with-an-asynchronous-call)
-  [Data Structure](#data-structure)
-  [Image Files](#image-files)
-  [Road Map](#road-map)
-  [Recent Changes](#road-map)

______________________

### Getting Started
Start by downloading the file, the project zip, or simply copy/paste the data directly into a file for your project.

### Top-Level Data Objects
Within the main Vainglory JSON object, there are currently 2 usable top-level data objects. The data for all of the heroes in the game can be accessed by using the JSON key `heroes`. The data for all of the items can be accessed by using the JSON key `items`.

### Accessing the Data (as a JavaScript object)
If you are using JavaScript, you can simply define the entire `vainglory.json` object as a value for a `var` or `const`, and avoid having to parse the data entirely.
```javascript
const vaingloryObject = {
    "items" : {...},
    "heroes" : {...}
};
```
With this method you can access the data like so:
```javascript
console.log(vaingloryObject.items.aegis.name);  // RETURNS: "Aegis"
console.log(vaingloryObject.heroes.adagio.name);  // RETURNS: "Adagio"
```

### Accessing the Data (with an Asynchronous call)
Many developers would prefer to call a file of this size asynchronously to better manage the UX and load times of their applications. To use this method, you would want to store the data as a file on your server, and use a server-side call to get the data and work with it.

##### If you're using jQuery in your project, you can call the data like so:
```javascript
// jQuery example of heroes key in use

var vainglory;
var vgGit = "data/vainglory.json";

var vgData = $.getJSON( vgGit, function(data) {
    
    vainglory = data;
    
});

// Access data like so:
console.log('Number of Heroes: ' + vainglory.heroes.length);
console.log('Number of Items: ' + vainglory.items.length);
```

##### If you're using standard JavaScript:
```javascript
// Pure JavaScript example of heroes key in use

const vainglory;
const vgGit = "data/vainglory.json";

const request = new XMLHttpRequest();
 
request.onreadystatechange = function() {
  
  if(request.readyState === 4) {
    
    if(request.status === 200) { 
      
      vainglory = request.responseText;
      
      // Access data like so:
      console.log('Number of Heroes: ' + vainglory.heroes.length);
      console.log('Number of Items: ' + vainglory.items.length);
      
    } else {
      
      console.log('An error occurred during your request: ' +  request.status + ' ' + request.statusText);
      
    }
    
  }
  
}
 
request.open('GET', vgGit);
```

### Data Structure
The structure of the JSON data in the vainglory.json file is as follows:
* items
  * item key
    * name
    * thumb
    * category
    * tier
    * cost
    * activate
    * passive
    * vampirism
    * bookofeulogies
    * armorbreaker
    * shieldbreaker
    * cosume
    * boots
    * travelboots
    * stormguard
    * breadth
    * depth
    * stats
      * health
        * value
        * name
        * units
      * health_recharge (same as health)
      * energy (same as health)
      * weapon_power (same as health)
      * crystal_power (same as health)
      * attack_speed (same as health)
      * armor (same as health)
      * shield (same as health)
      * range (same as health)
      * move_speed (same as health)
      * energy_recharge (same as health)
      * cooldown (same as health)
      * crit_chance (same as health)
      * crit_damage (same as health)
      * armor_pierce (same as health)
      * shield_pierce (same as health)
      * weapon_lifesteal (same as health)
      * crystal_lifesteal (same as health)
    * tip
    * build_from
    * build_to
* heroes
  * hero key
    * name
    * thumb
    * difficulty
    * attack_type
    * description
    * primary_role
    * ratings
      * offense
      * defense
      * team_utility
      * mobility
    * stats
      * health
        * name
        * units
        * min
        * max
      * health_recharge (same as health)
      * weapon_power
        * name
        * units
        * wp_scaling
        * min
        * max 
      * crystal_power
        * name
        * units
        * cp_scaling
        * min
        * max 
      * attack_speed (same as health)
      * armor (same as health)
      * shield (same as health)
      * energy (same as health)
      * energy_recharge (same as health)
      * cooldown
        * name
        * units
        * min
      * range (same as cooldown)
      * move_speed (same as cooldown)
      * crit_chance (same as cooldown)
      * crit_damage (same as cooldown)
      * armor_pierce (same as cooldown)
      * shield_pierce (same as cooldown)
      * weapon_lifesteal (same as cooldown)
      * crystal_lifesteal (same as cooldown)
    * abilities
      * heroic_perk
        * name
        * thumb
        * description
        * stat_levels
        * stats (currently false in all cases, but this is the object planned for future inclusion of calculatable stats for perk abilities)
      * a_ability
        * name
        * thumb
        * description
        * stat_levels
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * a_alt (currently for Malene only)
        * name
        * thumb
        * description
        * stat_levels
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * b_ability
        * name
        * thumb
        * description
        * stat_levels
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * b_alt (currently for Malene only)
        * name
        * thumb
        * description
        * stat_levels
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * c_ability
        * name
        * thumb
        * description
        * stat_levels
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive

### Image Files
The link below will provide you with a .zip file from a public dropbox directory. This .zip file has each image thumbnail referenced in the JSON data for each hero, each hero ability and each item. The organization of the image directories are as follows:
  * images
    * abilities
        * [directory with each heroes name]
    * heroes
    * items

<a href="https://www.dropbox.com/s/s2pqba48rghy0f5/images-vainglory-patch-3-6.zip?dl=0" target="_blank">Download Images Zip</a>

### Road Map
Here are the tasks planned for the future of this project:
1. Add in talent data for each hero

### Recent Changes
Here are the changes from the most recent release:
  * Added new hero SILVERNAIL and all his base stats and recommended builds!
  * Added Anka's Health Regen stats from vainglory site
  * Added Anka's Energy Regen stats from vainglory site
  * Updated Adagio's AGENT OF WRATH Damage 20/40/60/80/120 → 30/50/70/90/130
  * Updated Anka's MIRAGE Cooldown 60/45/30 → 60/50/40
  * Updated Catherine's MERCILESS PURSUIT Cooldown 14/13/12/11/10 → 16/15/14/13/12
  * Updated Celeste's HELIOGENESIS Supernova Damage 130/185/240/295/350 → 100/155/210/265/320
  * Updated Fortress's LAW OF THE CLAW Damage 70/115/160/205/250 → 70/100/130/160/190
  * Updated Grace's DIVINE INTERVENTION Cooldown 60/45/30 → 60/50/40
  * Updated Grumpjaw's LIVING ARMOR Damage Reduction 6% → 7%
  * Updated Gwen's SKEDADDLE Speed Boost Amount 1.2/1.4/1.6/1.8/2.2 → 2.5/2.8/3.1/3.4/4.0
  * Updated Gwen's SKEDADDLE Speed Boost Duration 1.5s → 2.2
  * Updated Kensei's KENSHO Cooldown 16/14.5/13/11.5/8.5 → 14/12/10/8/6
  * Updated Lance's GYTHIAN WALL Passive Damage Reduction 8/10/12/14/18% → 15/17.5/20/22.5/25%
  * Updated Lance's GYTHIAN WALL Crystal Ratio 20% → 12.5%
  * Updated Lance's GYTHIAN WALL Active Damage Reduction 40/44/48/52/56% → 40/45/50/55/60%
  * Updated Lance's GYTHIAN WALL Active Damage Reduction Crystal Ratio 20% → 15%
  * Updated Phinn's POLITE COMPANY Fortified life generated 140/170/200/230/290 → 120/145/170/195/245
  * Updated Reim's CHILL WINDS Root Duration 0.6/0.8/1.0/1.2/1.4 → 0.9/1.0/1.1/1.2/1.4
  * Updated Rona's STATS Attack Speed 100-113% → 100-122%
  * Updated Rona's BERSERKERS’ FURY Damage 80% → 85%
  * Updated Rona's FOESPLITTER Weapon Ratio 80% → 85%
  * Updated Rona's RED MIST Weapon Ratio 160% → 170%
  * Updated Tony's JAWBREAKER Damage 10/40/70/100/130 → 10/20/30/40/50
  * Updated Tony's JAWBREAKER Weapon Ratio 40% → 60%
  * Updated Tony's JAWBREAKER Stun duration 0.6s → 0.4/0.4/0.4/0.4/0.6s
  * Updated Tony's TRASH TALK Damage 30/45/60/75/90 → 50/90/130/170/210
  * Updated Varya's CHAIN LIGHTNING Secondary Target Crystal Ratio 30% → 35%
  * Updated Varya's ANVIL’S HAMMER Cooldown 120/105/90 → 90/75/60
  * Updated Vox's PULSE Bonus Resonance Damage 5/30/55/80/130 → 10/30/50/70/110
