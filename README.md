# Vainglory Base Stats v3.2.1.1
A JSON object master file, hard-coded from the game itself, for use in web-based applications that can parse JSON data.

______________________

## Table of Contents
-  [Getting Started](#getting-started)
-  [Top-Level Data Objects](#top-level-data-objects)
-  [Accessing the Data (as a JavaScript object)](#accessing-the-data-as-a-javascript-object)
-  [Accessing the Data (with an Asynchronous call)](#accessing-the-data-with-an-asynchronous-call)
-  [Data Structure](#data-structure)
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
    * stats
      * health
        * name
        * units
        * min
        * max
      * energy (same as health)
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
        * stats
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

### Road Map
Here are the tasks planned for the future of this project:
1. Add in all of the in-game recommended builds for each hero (requested by the community)
1. Add (or link to) a complete set of in-game images to this repository, to match the image file names used in this data!
1. Add in talent data for each hero

### Recent Changes
Here are the changes added during this release:
1. Addede in a data field for each hero to specify the attack type of a hero (IE melee, ranged, or melee/ranged)
1. Added in the difficulty rating for each hero (IE easy, medium, or hard)
1. Added in Energy Recharge and Health Recharge data for each hero (Note - this info is NOT in the game currently, and can only be found on the official game website. Many other stats on that website do NOT match the current in-game stats, but for now it's the best we've got!)
