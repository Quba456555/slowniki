# słowniki
def display_book(book):
    print("=" * 50)
    for key, value in book.items():
       print(f"{key}: {value}")
    print("=" * 50)

# Funkcja do edycji książki
def edit_book(book):
     print("Edytuj dane książki")
     print("=" * 50)
     display_book(book)
     print("=" * 50)
     key_to_edit = input("Podaj klucz, który chcesz edytować: ")
     if key_to_edit in book:
         new_value = input(f"Nowa wartość dla {key_to_edit}: ")
         book[key_to_edit] = new_value
         print("Dane zostały zaktualizowane.")
     else:
         print("Podany klucz nie istnieje.")

def delete_book(library, book_index):
    if 0 <= book_index < len(library):
        deleted_book = library.pop(book_index)
        print(f"Usunięto książkę (numer {book_index + 1}):")
        display_book(deleted_book)
        print("=" * 50)
    else:
        print("Podano nieprawidłowy numer książki do usunięcia.")


library = []  # Lista przechowująca słowniki reprezentujące książki

while True:
    print("=" * 50)
    print("1 - Dodaj nową książkę")
    print("2 - Wyświetl biblioteke")
    print("3 - Edytuj książkę")
    print("4 - Usuń książkę")
    print("5 - Wyjdź z programu")
    print("=" * 50)

    choice = input("Wybierz opcję: ")

    if choice == "1":
        new_book = {
            'tytuł': input("Podaj tytuł książki: "),
            'autor': input("Podaj autora książki: "),
            'liczba stron': input("Podaj liczbę stron książki: "),
            'rok wydania': input("Podaj rok wydania książki: ")
        }
        library.append(new_book)
        print("Książka została dodana do biblioteki.")

    elif choice == "2":
        for i, book in enumerate(library, 1):
            print(f"Książka {i}:")
            display_book(book)

    elif choice == "3":
        if not library:
            print("Biblioteka jest pusta. Dodaj książki przed edycją.")
        else:
            book_to_edit = int(input("Podaj numer książki do edycji: ")) - 1
            if 0 <= book_to_edit < len(library):
                edit_book(library[book_to_edit])
            else:
                print("Podano nieprawidłowy numer książki.")

    elif choice == "4":
        if not library:
            print("Biblioteka jest pusta. Dodaj książki przed usuwaniem.")
        else:
            book_to_delete = int(input("Podaj numer książki do usunięcia: ")) - 1
            delete_book(library, book_to_delete)

    elif choice == "5":
        print("Program zakończył działanie.")
        break

    else:
        print("Niepoprawny wybór. Wybierz opcję od 1 do 5.")
