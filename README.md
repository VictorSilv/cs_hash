# cs_hash
This library introduces dynamic data management in ChoiceScript


ChoiceScript Hash Table Library (cs_hash.txt) - Documentation
This library provides a hash table data structure for ChoiceScript games, allowing you to store and manage key-value pairs efficiently. It includes functions for insertion, retrieval, deletion, and table management while handling collisions by overwriting existing keys.

📖 Table of Contents

✨ Features
======================================================
📥 Installation
======================================================
🎮Usage & Examples
  1 - Initializing a Hash Table
  2 - Setting Key-Value Pairs
  3 - Retrieving Values
  4 - Deleting Entries
  5 - Clearing the Table
  6 - Checking Table Size
  7 - Printing Table Contents

======================================================

⚠️ Behavior with Duplicate Keys

🚨 Error Handling

💡 Best Practices

✨ Features
✅ Dynamic Key-Value Storage – Store and retrieve data using unique keys.
✅ Automatic Overwrite – If a key already exists, its value is updated (no duplicates).
✅ Deletion with Compaction – Removes entries and shifts remaining data to fill gaps.
✅ Table Clearing – Reset the entire hash table.
✅ Size Tracking – Check how many entries are stored.
✅ Debugging Tools – Print table contents for inspection.

📥 Installation
 Just copy and paste the  cs_hash.txt file into your ChoiceScript game "scenes" folder.

call it in your game file using:

 "*gosub_scene cs_hash" routines in orger to call the hash table functions in your game.

🎮 Usage & Examples
1. Initializing a Hash Table
Before using a hash table: Thou must initialize it with a array name <a string!> it's array size <number>.

For exmaple the command below:
*gosub_scene cs_hash hash_table_init "inventory" 20  
Creates a table named inventory with space for 9 key-value pairs (since each pair takes 2 slots and the mtadata necessary for it to work is already occupying the first slot).

2. Setting Key-Value Pairs
Use hash_table_set to add or update entries.



*gosub_scene cs_hash hash_table_set "inventory" "sword" "Excalibur"  


*gosub_scene cs_hash hash_table_set "inventory" "potion" "Health Potion"  


Note that, if "sword" already exists, its value is overwritten with "Excalibur".

3. Retrieving Values
Use hash_table_get to fetch a value by key.

*gosub_scene cs_hash hash_table_get "inventory" "sword"  
*if return = "KEY_NOT_FOUND"  
  You don't have a sword.  
*else  
  Your sword: ${return} (it should print "Excalibur")  
  
4. Deleting Entries
Remove a key-value pair with hash_table_delete.



*gosub_scene cs_hash hash_table_delete "inventory" "potion" 

*if return = "DELETED"  
  You used the potion! 
  
The table automatically compacts to fill the gap.

5. Clearing the Table
Reset all entries with hash_table_clear.



*gosub_scene cs_hash hash_table_clear "inventory"  

6. Checking Table Size
Get the number of entries with hash_table_size.



*gosub_scene cs_hash hash_table_size "inventory"  
*if return = 0  
  Your inventory is empty!  
  
7. Printing Table Contents (Debugging)
Display all stored data with hash_table_print. (very useful when testing your game!)

*gosub_scene cs_hash hash_table_print "inventory"  

Example output:



Table: inventory (2/10 entries)  
[0] Key: sword → Value: Excalibur  
[1] Key: potion → Value: Health Potion  


⚠️ Behavior with Duplicate Keys
If you hash_table_set a key that already exists, the old value is overwritten.

No duplicate keys are created.

Example:



*gosub_scene cs_hash hash_table_set "stats" "strength" 10  

*gosub_scene cs_hash hash_table_set "stats" "strength" 15  

more code here... 
them,

*gosub_scene cs_hash hash_table_get "stats" "strength"  

Output of ${return} will be: 15 (the original 10 was replaced).

🚨 Error Handling
Hash Table Full: If you exceed the maximum size, hash_table_set logs:



*bug HASH_TABLE_FULL: "inventory current_index: 23"  
Key Not Found: hash_table_get and hash_table_delete return "KEY_NOT_FOUND".

💡 Best Practices
✔ Initialize Once – Call hash_table_init only once per table.
✔ Check for Key Existence – Always verify return after hash_table_get.
✔ Use Meaningful Keys – Avoid numeric keys (e.g., "item_1" instead of 1).
✔ Monitor Size – Use hash_table_size to prevent overflows. (!!)

🎉 Conclusion
This library simplifies dynamic data management in ChoiceScript, making it ideal for:

*Inventories!

*Player Stats!

*Quest Tracking!

*Dynamic Story Flags!

Try it out and let me know if you need enhancements! ::Rocket::

📜 Full Code: cs_hash.txt (Paste into your scenes folder)

❓ Questions? Ask the guys at Choice of Games Forum!
