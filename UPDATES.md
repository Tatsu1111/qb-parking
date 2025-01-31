## ---------------------------------------------Updates------------------------------------------------
- Again a huge update, added parking time expired, when this happens the vehicle wil be impounded automatically by the police.
- Added a max amount of parking vehicles per player.
- Added a max amount of parking vehicles on the server.

## NOTE
- If you have 10 players make the max amount on the server 10 and 1 for each player.
- if you have add 5 for max on the server, and you add 5 for each player, than you can only park the max amount the server allowed.


## Removed
- polyzone removed, cause we dont need it, we have parking locations that are pre-created.
- we have a max amount the server allowed, and a max amount that a player can park vehicles.
- so and to minimize the prosses on the server i put addedthis to the system.
- in this case you can't ovelroad your server with parked vehicles.


## Database Table Change
- New database table
```sql
CREATE TABLE IF NOT EXISTS `player_parking_vehicles` (
  `id` int(10) NOT NULL AUTO_INCREMENT,
  `citizenid` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `citizenname` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `model` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `modelname` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `plate` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL,
  `fuel` int(15) NOT NULL DEFAULT 0,
  `engine` int(15) NOT NULL DEFAULT 0,
  `body` int(15) NOT NULL DEFAULT 0,
  `oil` int(15) NOT NULL DEFAULT 0,
  `data` longtext COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `coords` longtext COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  `time` bigint(20) NOT NULL,
  `cost` int(10) NOT NULL DEFAULT 0,
  `parktime` int(10) NOT NULL DEFAULT 0,
  `parking` varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
  PRIMARY KEY (`id`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci ROW_FORMAT=DYNAMIC;
```

- or use this, if you already have the database table
- but, check if you are not already have the columns inside your table....
- you can also remove the table and add the new table. but below this 
```sql
ALTER TABLE `player_parking_vehicles` ADD COLUMN `time` BIGINT(20) AFTER `coords`;
ALTER TABLE `player_parking_vehicles` ADD COLUMN `engine` INT(15) AFTER `fuel`;
ALTER TABLE `player_parking_vehicles` ADD COLUMN `body` INT(15) AFTER `engine`;
ALTER TABLE `player_parking_vehicles` ADD COLUMN `oil` INT(15) AFTER `body`;
ALTER TABLE `player_parking_vehicles` ADD COLUMN `cost` INT(15) AFTER `time`;
ALTER TABLE `player_parking_vehicles` ADD COLUMN `parktime` INT(15) AFTER `cost`;
ALTER TABLE `player_parking_vehicles` ADD COLUMN `parking` VARCHAR(255) AFTER `parktime`;

```


## Server Performance
- Config.UseMaxParkingPerPlayer    = true         -- Default true if you want to use a max amount of parked vehicles per player
- Config.MaxStreetParkingPerPlayer = 1            -- Default 1, total allowed parked vehicles per player in world
- Config.UseMaxParkingOnServer     = true         -- Default true if you want to use a max amount of vehicles that can park on the server.
- Config.MaxServerParkedVehicles   = 50           -- Default 50, total allowed parked vehicles on the server.



## 😎 Special thanks for helping me with testing 👊😉👍
- 💪 GUS
- 💪 Jazerra
- 💪 ameN
- 💪 MulGirtab
- 💪 DannyJ
- 💪 MasonJason310
- 💪 Enxsistanz
- 💪 !ExiledVibe!
- 💪 FARRUKO

## 🙈 My Youtube & My Discord 👊😉👍
- [Youtube](https://www.youtube.com/channel/UC6431XeIqHjswry5OYtim0A)
- [Discord](https://discord.gg/cEMSeE9dgS)
