# Vainglory Base Stats v3.2.1.0
A JSON object master file, hard-coded from the game itself, for use in web-based applications that can parse JSON data.

### Getting Started
Start by downloading the file, the project zip, or simplay copy/pasting the data directly into a file for your project.

### Accessing the Data (as a JavaScript object)
If you are using JavaScript, you can simply define the entire `vainglory.json` object as a value for a var or const, and avoid having to parse the data entirely.
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

### Accessing the Data (as an Asynchronous call)
Within the main Vainglory JSON object, there is currently 2 usable data sets. The data for heroes can be accessed by using the JSON key `heroes`. The data for items can be accessed by using the JSON key `items`.
```javascript
// jQuery example of heroes key in use

var vainglory;
var vgGit = "data/vainglory.json";
var vgData = $.getJSON( vgGit, function(data) {
    vainglory = data;
});

console.log('Number of Heroes: ' + vainglory.heroes.length);
console.log('Number of Items: ' + vainglory.items.length);
```

```javascript
// Pure JavaScript example of heroes key in use

var vainglory;
var vgGit = "data/vainglory.json";

var request = new XMLHttpRequest();
 
request.onreadystatechange = function() {
  if(request.readyState === 4) {
    if(request.status === 200) { 
      vainglory = request.responseText;
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
    * description
    * stats
      * health
        * name
        * units
        * min
        * max
      * energy (same as health)
      * weapon (same as health)
      * attack_speed (same as health)
      * armor (same as health)
      * shield (same as health)
      * range
        * name
        * units
        * min
      * move_speed (same as range)
      * energy_recharge (same as health)
      * cooldown (same as range)
      * crit_chance (same as range)
      * crit_damage (same as range)
      * armor_pierce (same as range)
      * shield_pierce (same as range)
      * weapon_lifesteal (same as range)
      * crystal_lifesteal (same as range)
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
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * a_alt (currently for Malene only)
        * name
        * thumb
        * description
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * b_ability
        * name
        * thumb
        * description
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * b_alt (currently for Malene only)
        * name
        * thumb
        * description
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive
      * c_ability
        * name
        * thumb
        * description
        * stats (same for each stat)
          * name
          * values
          * ratios
          * overdrive


