import random

def choose_word():
    # Lista de palabras posibles
    words = ['python', 'hangman', 'challenge', 'programming', 'developer', 'artificial', 'intelligence']
    return random.choice(words)

def display_word(secret_word, guessed_letters):
    # Muestra las letras adivinadas o _ si no se han adivinado
    return ' '.join([letter if letter in guessed_letters else '_' for letter in secret_word])

def hangman():
    secret_word = choose_word()  # Palabra secreta elegida aleatoriamente
    guessed_letters = set()      # Letras adivinadas hasta ahora
    tries = 6                    # Número de intentos permitidos

    print("🎮 ¡Bienvenido al juego del Ahorcado!")
    print(f"La palabra tiene {len(secret_word)} letras.")

    # Bucle del juego
    while tries > 0:
        print("\nPalabra: ", display_word(secret_word, guessed_letters))
        print(f"Intentos restantes: {tries}")
        guess = input("Adivina una letra: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("❌ Por favor ingresa solo una letra.")
            continue

        if guess in guessed_letters:
            print("⚠️ Ya has adivinado esa letra.")
            continue

        guessed_letters.add(guess)

        if guess not in secret_word:
            print("❌ Letra incorrecta.")
            tries -= 1
        else:
            print("✅ ¡Bien hecho!")

        # ¿Ganó?
        if all(letter in guessed_letters for letter in secret_word):
            print("\n🎉 ¡Felicidades! Has adivinado la palabra:", secret_word)
            break
    else:
        print("\n💀 Has perdido. La palabra era:", secret_word)

if __name__ == "__main__":
    hangman()
