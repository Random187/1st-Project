# Iedvesmas avots:  https://www.codegrepper.com/code-examples/python/python+hangman

import random
import time

# Initial Steps to invite in the game:
print("\nEsiet sveicināti 'Karātavu' spēlē\n")
name = input("Ievadiet savu vārdu: ")
print("Sveiks " + name + "! Vēlam veiskmi!")
time.sleep(2)
print("Spēle sākas!\nSākam spēli 'Karātavas'!\nJums ir jāuzmin nejauši izvēlēts vārds!")
time.sleep(3)


# The parameters we require to execute the game:
def main():
    global count
    global display
    global word
    global already_guessed
    global length
    global play_game
    words_to_guess = ["saule","mēness","jūra","filma","mežš","sirds","acis","debesis","mūzika","bungas","augļi"]
    word = random.choice(words_to_guess)
    length = len(word)
    count = 0
    display = '_' * length
    already_guessed = []
    play_game = ""

# A loop to re-execute the game when the first round ends:

def play_loop():
    global play_game
    play_game = input("Vai vēlaties spēlēt vēlreiz? y = Jā, n = Nē \n")
    while play_game not in ["y", "n","Y","N"]:
        play_game = input("Vai vēlaties spēlēt vēlreiz? y = Jā, n = Nē \n")
    if play_game == "y":
        main()
    elif play_game == "n":
        print("Paldies par piedalīšanos! Gaidīsim Jūs atkal!")
        exit()

# Initializing all the conditions required for the game:
def hangman():
    global count
    global display
    global word
    global already_guessed
    global play_game
    limit = 5
    guess = input("Šis ir 'Karātavu' nejauši izvēlētais vārds: " + display + " Ievadie savu minējumu: \n")
    guess = guess.strip()
    if len(guess.strip()) == 0 or len(guess.strip()) >= 2 or guess <= "9":
        print("Nepareiza ievade, Pamēģiniet burtu\n")
        hangman()


    elif guess in word:
        already_guessed.extend([guess])
        index = word.find(guess)
        word = word[:index] + "_" + word[index + 1:]
        display = display[:index] + guess + display[index + 1:]
        print(display + "\n")

    elif guess in already_guessed:
        print("Pamēģiniet citu burtu.\n")

    else:
        count += 1

        if count == 1:
            time.sleep(1)
            print("   _____ \n"
                  "  |      \n"
                  "  |      \n"
                  "  |      \n"
                  "  |      \n"
                  "  |      \n"
                  "  |      \n"
                  "__|__\n")
            print("Nepareizs minējums." + str(limit - count) + " atlikušie minējumi ir\n")

        elif count == 2:
            time.sleep(1)
            print("   _____ \n"
                  "  |     | \n"
                  "  |     |\n"
                  "  |      \n"
                  "  |      \n"
                  "  |      \n"
                  "  |      \n"
                  "__|__\n")
            print("Nepareizs minējums. " + str(limit - count) + " atlikušie minējumi ir\n")

        elif count == 3:
           time.sleep(1)
           print("   _____ \n"
                 "  |     | \n"
                 "  |     |\n"
                 "  |     | \n"
                 "  |      \n"
                 "  |      \n"
                 "  |      \n"
                 "__|__\n")
           print("Nepareizs minējums. " + str(limit - count) + " atlikušie minējumi ir\n")

        elif count == 4:
            time.sleep(1)
            print("   _____ \n"
                  "  |     | \n"
                  "  |     |\n"
                  "  |     | \n"
                  "  |     O \n"
                  "  |      \n"
                  "  |      \n"
                  "__|__\n")
            print("Nepareizs minējums. " + str(limit - count) + " atlicis pēdējais minējums\n")

        elif count == 5:
            time.sleep(1)
            print("   _____ \n"
                  "  |     | \n"
                  "  |     |\n"
                  "  |     | \n"
                  "  |     O \n"
                  "  |    /|\ \n"
                  "  |    / \ \n"
                  "__|__\n")
            print("Nepareizs minējums. Spēles beigas !!!\n")
            print("Atminamais vārds bija:",already_guessed,word)
            play_loop()

    if word == '_' * length:
        print("Apsveicam! Jūs esat atminējuši pareizi vārdu!")
        play_loop()

    elif count != limit:
        hangman()


main()


hangman()
