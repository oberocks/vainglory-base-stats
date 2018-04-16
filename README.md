# Vainglory Base Stats
A JSON object master file, hard-coded from the game itself, for use in web-based applications that can parse JSON data.


### Accessing the Data
Within the main Vainglory JSON object, there is currently 1 usable data set (an items data set is planned in the future). This data is accessed with a key named `heroes`.
```javascript
// jQuery example of heroes key in use

var vainglory;
var vgGit = "https://gitcdn.link/repo/oberocks/vainglory-base-stats/master/vainglory.json";
var vgData = $.getJSON( vgGit, function(data) {
    vainglory = data;
});

console.log('Number of Heroes: ' + vainglory.heroes.length);
```

```javascript
// Pure JavaScript example of heroes key in use

var vainglory;
var vgGit = "https://gitcdn.link/repo/oberocks/vainglory-base-stats/master/vainglory.json";

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
The structure of the JSON data is the vainglory.json file is as follows:
* items
* heroes
  * slug
  * name
  * thumb
  * description
  * stats
    * health
      * min
      * max
    * energy
      * min
      * max
    * weapon
      * min
      * max
    * atkspeed
      * min
      * max
    * armor
      * min
      * max
    * shield
      * min
      * max
    * range
    * movespeed
  * abilities
    * heroicperk
      * name
      * thumb
      * description
    * a
      * name
      * thumb
      * description
      * stats
        * name
        * values
        * ratios
        * overdrive
    * b
      * name
      * thumb
      * description
      * stats
        * name
        * values
        * ratios
        * overdrive
    * c
      * name
      * thumb
      * description
      * stats
        * name
        * values
        * ratios
        * overdrive


### Data Types
The data types you will get returned are formatted as follows:
* items (Coming Soon!)
* heroes
  * slug (String)
  * name (String)
  * thumb (String)
  * description (Array containing items that are either strings or 1 nested array of only strings)
  * stats
    * health
      * min (Number)
      * max (Number)
    * energy
      * min (Number)
      * max (Number)
    * weapon
      * min (Number)
      * max (Number)
    * atkspeed
      * min (Number)
      * max (Number)
    * armor
      * min (Number)
      * max (Number)
    * shield
      * min (Number)
      * max (Number)
    * range (Number)
    * movespeed (Number)
  * abilities
    * heroicperk
      * name (String)
      * thumb (String)
      * description (Array containing items that are either strings or 1 nested array of only strings)
    * a
      * name (String)
      * thumb (String)
      * description (Array containing items that are either strings or 1 nested array of only strings)
      * stats
        * name (String)
        * values (Array of 5 Numbers)
        * ratios (Array of 2 Numbers)
        * overdrive (Either a boolian false value or a Number match to a values array Number for this stat)
    * b
      * name (String)
      * thumb (String)
      * description (Array containing items that are either strings or 1 nested array of only strings)
      * stats
        * name (String)
        * values (Array of 5 Numbers)
        * ratios (Array of 2 Numbers)
        * overdrive (Either a boolian false value or a Number match to a values array Number for this stat)
    * c
      * name (String)
      * thumb (String)
      * description (Array containing items that are either strings or 1 nested array of only strings)
      * stats
        * name (String)
        * values (Array of 5 Numbers)
        * ratios (Array of 2 Numbers)
        * overdrive (Either a boolian false value or a Number match to a values array Number for this stat)
