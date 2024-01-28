# DEX-sans-spiders
Daggerfall Enemy Expansion addon to removes spiders

This project also serves as an example of how to make an addon for [Daggerfall Enemy Expansion](https://www.nexusmods.com/daggerfallunity/mods/372). 
DEX is a flexible, data-driven mod. Almost all the features come from simple text files, and DEX can find and read files from other mods. 
Other mods can therefore add new classes and enemies, modify enemies (whether classic or new to DEX), and handle other features like encounter tables and equipment.

Therefore, by looking at the files in the repository, one can have an idea of how this process operates.

## Setup

The first part of any mod is making your own Github reposity. Even if you already have a repo for another mod, creating a new one for each mod is cleaner. For example, a contributor that wants to help with only one of your mod does not have to bloat their DFU installation with your other projects.

A guide for repo creation can be found here: https://docs.github.com/en/repositories/creating-and-managing-repositories/quickstart-for-repositories

After creating the repo, you will need to "clone" it (make a copy) on your machine. Again, Github has guides for this: https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository. You may want to use a GUI tool for Git like Github Desktop or Git Extensions rather than commandline tools.

The important part is _where_ you will clone your mod. Assuming you have already cloned [Daggerfall Unity](https://github.com/Interkarma/daggerfall-unity), the location where you will clone your mod is under DFU's Assets/Game/Mods.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/bdc57ca0-7fe4-4584-846f-c4bee1204128)

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/d8779c8a-56a0-4230-84d0-80f480cc7486)

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/ff73e773-0032-4af0-925a-67daaac180b6)

(See how nice Git Extensions can be).

Try to avoid renaming the folder after creation. It's better if the default name is correct, because everyone who clones your repo needs to keep the same name (because of how .dfmod.json stores paths).

Once the repo exists on your computer, it is time to create the mod files. Go back to Unity, and select Daggerfall Tools at the top, then Mod Builder.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/c4f1662f-0622-49bd-b4af-fc14894709fd)

From the Mod Builder, click Create New Mod on the top-left, select your folder, and give your mod config file a name. That name is not too important, the mod itself can have its own name later.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/5959b284-491e-481d-87dd-d0bc5521fe1a)

You can now fill out the rest of the fields.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/9e1b245a-f07e-4c5a-8b3c-cf7c1bf22f84)

Last step is to ensure you have a Dependency on DEX. Open the Dependencies Editor

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/5feb83a8-b24d-482f-a503-9d3114ce666a)

Click Add Dependency, then enter "daggerfall enemy expansion.dfmod", and ensure the Requirement is left to "Is Required for core functionalities".

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/b51fa36a-1a3e-4fcf-b957-5453798aae7e)

Click Save and Close.

Finally, after all this, make sure to click Save Settings to Mod File!

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/8cff4fb8-9ff1-4229-80d8-ef442438e3cf)

We are now set up to make the mod.

## Working with DEX

DEX has multiple "database" types. Here are the types:

- "Enemy" database (.mdb.csv), which contains data on new or modified enemies (whether monster or "class" type)
- "Career" database (.cdb.csv), which contains data on "careers" used by an enemy (this is what DFU calls a character class)
- "Encounter Table" database (.tdb.csv), which contains encounter tables

Each file has entries identified by an ID, then a bunch of properties associated with the entry. When creating a new entry (new enemy, career, or encounter table), some fields might be required. When modifying an existing entry (from another mod), only the ID and the properties you want to change are necessary. 

For each file you create for your mod, don't forget to add it to your mod through the Mod Builder.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/56688ae0-c768-48da-874d-e44c7ad5ece7)

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/2c534de2-3f2b-4666-885a-49a38581f748)

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/45bb4d46-ad46-4d33-8777-c64d21d300b0)

Your .dfmod.json file should have the new file listed in this section.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/654f40d0-bcc3-4653-9d6b-d1f4eb7f9c0b)

### Career database
Since all enemies need a career, this might be the first one you deal with. A career database can specify new careers for enemies, or career replacements for existing careers (both classic or modded). To create one, create a file with any name and the extension `.cdb.csv` (ex: `new_careers.cdb.csv`). 

Careers are identified by the name column. That column is required in every .cdb.csv file, and should be the first column. When adding new careers, the columns 'HitpointsPerLevel', 'Strength', 'Intelligence', 'Willpower', 'Agility', 'Strength', 'Personality', 'Speed', and 'Luck' are required, and all entries should have a valid value in those columns.

Here's an example of a database with new careers: https://github.com/SquidKamer/DaggerfallBestiaryProject/blob/main/CareerBase.cdb.csv

Here's an example of a database with classic career replacements: TODO

Classic careers are often identified by the English enemy name without spaces (ex: GiantScorpion, OrcSergeant, IceAtronach, Mage, Barbarian, ...). The guards' career is identified with the name "Guard", despite DFU code referring to its as "Knight_CityWatch".

### Enemy database

New enemies and enemy replacements go into these monster database files. DFU distinguishes between "monster" and "class" enemies - the former being regular monsters like rats, orcs, giants, and trolls, and "class" enemies being the enemies based on a player class (ex: Mage, Thief, Barbarian, Monk, Guard). DEX puts both in the same monster databses, though you might want to put them in separate files if you want. To create one, create a file with any name and the extension `.mdb.csv` (ex: `new_monsters.mdb.csv`). 

Enemies are identified with a numeric ID. When creating a new enemy, you need to invent a new number that is not used by DFU or any other mod, then put that in the first column. Note, not all IDs are the same! In the original DF data, enemies between 0 and 127 are monsters, and enemies between 128 and 256 are "class" enemies. DFU expands this: for each multiple of 256, the first 128 are monsters, and the second 128 are enemies.

To reserve an id range for your mod, multiply 256 by any number. The result will give you 128 monster ids, and 128 class ids. For example, DEX uses 256*1=256, and all numbers between 256 and 511 are reserved for DEX enemies. Numbers between 256 and 383 are monsters, and numbers between 384 and 511 are class. If you need more, just find a new range for your mod.

Here's an example of a database with new monsters: https://github.com/SquidKamer/DaggerfallBestiaryProject/blob/main/MonsterBase.mdb.csv

Here's an example of a database with new class enemies: https://github.com/SquidKamer/DaggerfallBestiaryProject/blob/main/ClassBase.mdb.csv

Here's an example of a database with class monster replacements: https://github.com/SquidKamer/DaggerfallBestiaryProject/blob/main/ClassicMonsterReplacement.mdb.csv

Classic enemies ids can be found in the following DFU file: https://github.com/Interkarma/daggerfall-unity/blob/master/Assets/Scripts/Utility/EnemyBasics.cs. Simply search the enemy name you're looking for with a // in front of it (ex: CTRL+F "// Dreugh") and get the id under it

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/08001068-4490-4133-b5cb-0455cdd15da6)

For DEX Sans Spiders, we do the following replacement.

![image](https://github.com/KABoissonneault/DEX-sans-spiders/assets/5789925/216577d0-0b59-49b4-9eaf-25a64bdea1cd)

For id 6 (classic Spider) and 271 (DEX's Blood Spider), we replacement the textures and sounds with the lizards (similar attack properties, not too confusing).

And the mod is finished!

### Encounter table database

TODO
