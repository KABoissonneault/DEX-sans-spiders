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

The important part is _where_ you will clone your mod. Assuming you have already cloned [Daggerfall Unity](https://github.com/Interkarma/daggerfall-unity), the location where you will clone your mod is under Assets/Game/Mods.

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

We are now setup to make the mod.
