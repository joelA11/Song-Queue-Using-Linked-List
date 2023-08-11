This C program implements a simple song queue management system using a singly linked list data structure. The purpose of the project is to allow users to manage and interact with a playlist of songs. Here's a breakdown of what the program does:

1. **Data Structure Definition:**
   The program defines a structure named `Node` that represents a song node in the linked list. Each node contains the name of the song (`song`) and a pointer to the next node (`next`).

2. **Function Definitions:**
   The program provides various functions to manipulate the song queue:
   
   - `makeNode`: Creates a new node with the given song name.
   - `display`: Recursively displays the songs in the queue along with their position.
   - `insertHead`: Inserts a song at the beginning of the queue.
   - `insertEnd`: Inserts a song at the end of the queue.
   - `insertAt`: Inserts a song at a specified position in the queue.
   - `deleteHead`: Removes the first song from the queue.
   - `deleteEnd`: Removes the last song from the queue.
   - `deleteAt`: Removes a song from a specified position in the queue.
   - `currentSong`: Displays the currently playing song.
   - `countSongs`: Counts the number of songs in the queue.
   - `disRandom`: Selects and displays a song randomly from the queue.

3. **Main Menu Loop:**
   The `main` function initializes the linked list and presents a menu with several options for interacting with the song queue:
   
   - Display the entire song queue.
   - Show the current playing song.
   - Add a song to the end of the queue.
   - Add a song to play next.
   - Add a song at a specific position in the queue.
   - Delete the last song from the queue.
   - Delete the currently playing song.
   - Delete a song at a specific position in the queue.
   - Get the total number of songs in the queue.
   - Play a song randomly from the queue.
   - Exit the program.

4. **User Interaction:**
   Users can choose options from the menu to perform actions on the song queue. Depending on the chosen option, the program calls the relevant functions to manipulate the linked list accordingly. For instance, users can add, delete, display, and shuffle songs in the queue.

5. **Exiting the Program:**
   The program runs in an infinite loop, allowing users to perform multiple operations. Users can choose the "Exit" option from the menu to terminate the program.

In summary, this project provides a basic interactive environment for managing a playlist of songs using a linked list data structure. Users can add, delete, display, and shuffle songs within the queue through a user-friendly menu-driven interface.
