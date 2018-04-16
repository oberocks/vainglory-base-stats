# Vainglory Base Stats
A JSON object master file, hard-coded from the game itself, for use in web-based applications that can parse JSON data.

### Access & Structure
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
