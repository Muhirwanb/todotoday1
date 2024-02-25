#!/usr/bin/env python3

import sys, json, shutil

#beginning lists used for the to-do list
todo = []

todone = []

#function for displaying the to-do list on separate lines
def betterprint():
    #calculates terminal size and list sizes to keep window clean
    lines = shutil.get_terminal_size()
    height = lines[1]
    height = int(height)
    negheigt = len(todo) + len(todone) + 6
    numofprints = height - negheigt
    #format for printing of lists
    print("~~~~~~~~~~~~~~~~~~~")
    print("To-do:")
    for x in todo:
        print(x)
    print("~~~~~~~~~~~~~~~~~~~")
    print("To-done:")
    for x in todone:
        print(x)
    print("~~~~~~~~~~~~~~~~~~~")
    for i in range(numofprints):
        print("")


#functions to save and open to-do lists
def savetodo():
    global todo
    with open('todolist.txt', 'w') as filehandle:
        json.dump(todo, filehandle)
    print("Saved, to-do list!")

def opentodo():
    global todo
    with open('todolist.txt', 'r') as filehandle:
        todo = json.load(filehandle)
    betterprint()

#help function
def helper():
    print("Command:     add       adds to list.")
    print("Command:     done      removes a task from the list.")
    print("Command:     todo      displays the current to-do list.")
    print("Command:     help      displays this help message.")
    print("Command:     save      saves the current list.")
    print("Command:     clear     clears the specified list, either \'--t\' for To-do or \'--d\' for To-done.")
    print("Command:     purge     clears all lists")
    print("Command:     quit      exit To-do To-day.")


#functions to clear lists
def cleardone():
    global todone
    todone = []
    print("Cleared completed tasks.")

def cleartodo():
    global todo
    todo = []
    print("Cleared to-do list.")

def purgeall():
    global todone, todo
    todone = []
    todo = []
    print("All lists reset.")


#main function
def starting():
    getit = input(">>> ")
    if "add" in getit:
        task = getit[3:]
        todo.append(task)
        betterprint()
        starting()
    elif "done" in getit:
        done = getit[4:]
        for todotask in todo:
            if todotask == done:
                todo.remove(done)
                n = len(done)
                for l in done:
                    done = done + l + '\u0336'
                todone.append(done[n:])
                print(">>> To-do? To-done!")
        betterprint()
        starting()
    elif getit == "help":
        helper()
        starting()
    elif getit == "save":
        savetodo()
        starting()
    elif getit == "quit":
        print("Are you sure you want to quit [Y/N]?")
        yn = input(">>>")
        if yn.upper() == "Y":
            savetodo()
            sys.exit()
        else:
            starting()
    elif getit == "todo":
        betterprint()
        starting()
    elif getit == "clear --t":
        cleartodo()
        betterprint()
        starting()
    elif getit == "clear --d":
        cleardone()
        betterprint()
        starting()
    elif getit == "purge":
        purgeall()
        starting()
    else:
        print("Unknown command. Type \'help\' to see available commands.")
        starting()

#Main script sequence
opentodo()

starting()
