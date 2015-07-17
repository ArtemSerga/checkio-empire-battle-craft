**Example:**

```javascript
var Client = require("battle/commander.js").Client;
var client = new Client();

function attackNearest() {
    client.askNearestEnemy(function (data) {
        client.doAttack(data.id);
        client.whenItemDestroyed(data.id, attackNearest);
    });
}

client.askMyInfo(function () {
    attackNearest();
});
```