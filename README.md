# Vainglory Base Stats
A JSON object master file, hard-coded from the game itself, for use in web-based applications that can parse JSON data.


### Accessing the Data
Within the main Vainglory JSON object, there is currently 1 usable data set (an items data set is planned in the future). This data is accessed with the key `heroes`.
```javascript
// jQuery example of heroes key in use

var vainglory;
var vgGit = "data/vainglory.json";
var vgData = $.getJSON( vgGit, function(data) {
    vainglory = data;
});

console.log('Number of Heroes: ' + vainglory.heroes.length);
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
    } else {
      console.log('An error occurred during your request: ' +  request.status + ' ' + request.statusText);
    } 
  }
}
 
request.open('GET', vgGit);
```

### Data Structure
The structure of the JSON data in the vainglory.json file is as follows:
* items (Coming Soon!)
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


