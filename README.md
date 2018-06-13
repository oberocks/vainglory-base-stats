# Vainglory Base Stats v3.3.1.2
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

<a href="https://www.dropbox.com/s/w2jp7nlehesjobe/vg-images-patch-3-4.zip?dl=0" target="_blank">Download Images Zip</a>

### Road Map
Here are the tasks planned for the future of this project:
1. Add in talent data for each hero

### Recent Changes
Here are the changes from the most recent release:
  * fixed missing move speed number for "war_treads" in "items"
  * fixed "lyra" "ability_c" stat levels (changed from 5 to 3)
  * fixed "skye" recommend weapon build from spellfire to spellsword
  * added in health and energy regen data for "malene" and "kensei" (from vainglorygame.com)
  * added in new hero "kenetic" and all data for this hero
  * removed "echo" item and data
  * added "pulseweave" item and data
  * added "capacitor_plate" item and data
  * added "rooks_decree" item and data
  * changed "aftershock" cooldown to 15
  * changed "chronograph" cooldown to 10
  * changed "clockwork" cooldown to 20
  * changed "contraption" cooldown to 20
  * changed "crystal_infusion" cooldown to 5-15
  * changed "halcyon_chargers" cooldown to 10
  * changed "hourglass" cooldown to 5
  * changed "nullwave_gauntlet" cooldown to 15
  * changed "scoutpak" cooldown to 10
  * changed "spellsword" cooldown to 20
  * added +0.1 move_speed to each hero's base stat
  * updated "baptiste" bad mojo damage and splash damage crystal ratios
  * updated "catherine" merciless pursuit cooldown
  * updated "catherine" blast tremor silence duration and cooldown
  * updated "churnwalker" Futility of Life percentage
  * updated "churnwalker" Tresspass text per rework
  * updated "fortress" truth of the tooth damage and speed boost
  * updated "fortress" law of the claw percent damage
  * updated "grace" divine intervention cooldown
  * updated "kensei" base weapon power stats 
  * updated "kensei" immovable mind data 
  * updated "kensei" path of the ronin stun duration 
  * updated "kestrel" glimmer shot splash damage crystal ratio
  * updated "lyra" imperial sigil text data for heal
  * updated "lyra" bright bulwark duration
  * updated "lorelai" added WATER DENIZEN perk to her text 
  * updated "lorelai" fish food cast time number 
  * updated "malene" enchanted transformation damage
  * updated "malene" enchanted transformation crystal ratio
  * updated "malene" enchanted transformation cooldown
  * updated "phinn" heroic perk to include WATER DENIZEN
  * updated "reza" trouble maker bonus damage crystal ratio 
  * updated "samuel" malice & verdict empowered damage crystal ratio 
  * updated "skye" suri strike cooldown
  * updated "taka" heroic perk rework text
  * updated "taka" x-retsu damage weapon ratio
  * updated boots items ("sprint_boots", "travel_boots", "journey_boots", "war_treads", & "halcyon_chargers") with -0.1 movement speed
  * NOTE: according to the game... "teleport_boots" move speed did not go down by 0.1 and is still at 0.5 which matches "journey_boots" for the most move speed added per item
  * updated "aftershock" next basic attack damage percentage
  * updated "alternating_current" attack speed 
  * updated "bonesaw" attack speed 
  * NOTE: updated "capacitor_plate" in-game is missing the stat of 2.5 energy regen which is stated in the notes - have included in this data as stated in the notes and NOT the game
  * updated "coat_of_plates" shield amount 
  * updated "clockwork" text data 
  * updated "fountain_of_renewal" health amount
  * updated "kinetic_shield" armor
  * updated "lifespring" health 
  * updated "poisoned_shiv" attack speed
  * updated "shiversteel" attack speed
  * updated "slumbering_husk" with all of rework data
  * updated "tornado_trigger" with all of rework data
  * updated "weapon_infusion" text data
