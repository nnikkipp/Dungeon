# Dungeon
Hi there, thats one of the special tasks. It's like a game -> As a young adventurer, you seek gold and glory in the darkest dungeons there are. А game where every herо wins the day with shiny armor and a smile...

function dungeon (arr) {

    let health = 100;
    let coins = 0;
    let counterRooms = 0;

    let dungen = arr[0].split('|');

    let death = false;

    for (let i = 0; i < dungen.length; i++) {
        let currentRoom = dungen[i].split(' ');
        let command = currentRoom[0];
        let currentNumber = Number(currentRoom[1]);
        counterRooms++;

        if (command === "potion") {
            health += currentNumber;

            if (health > 100) {
                let left = 100 - health + currentNumber;
                console.log(`You healed for ${left} hp.`); 
                health = 100;
            } else {
                console.log(`You healed for ${currentNumber} hp.`); 
            }
            console.log(`Current health: ${health} hp.`);
        } else if (command === "chest") {
            coins += currentNumber;
            console.log(`You found ${currentNumber} coins.`);
        } else {
            health-=currentNumber;
            //console.log(health);
            if (health <= 0) {
                console.log(`You died! Killed by ${command}.`);
                console.log(`Best room: ${counterRooms}`);
                death = true;
                break;
            } else {
                console.log(`You slayed ${command}.`);
            }
        }
    }

    if (death === false) {
        console.log("You've made it!");
        console.log(`Coins: ${coins}`);
        console.log(`Health: ${health}`);
    }

}
