# Northwind database - MongoDB
Celem projektu było zaimplementowanie systemu realizującego wybrane, podstawowe operacje na przykładowej bazie Northwind, w wybranej technologii.

## Stos technologiczny
- **MongoDB** – nierelacyjny system do zarządzania bazą danych Northwind
- **Spring Boot + Java11** – serwis realizujący podstawowe operacje na bazie Northwind.
- **Swagger** – automatyczna dokumentacja metod RestAPI.
- **Docker** – konteneryzacja aplikacji.

## Schemat bazy danych
<img width="450" alt="Schemat" src="https://user-images.githubusercontent.com/34041060/129492965-a82a59f0-1ac1-4239-a86e-fd1f3c32f29c.png">

**Symulacja relacji w bazie danych nosql:**
- **Embedded way** - jeden dokument zostaje osadzony w innym dokumencie.
- **Reference approach** - dokumenty przechowywane są oddzielnie, ale jeden dokument zawiera odniesienie do pola id drugiego dokumentu.

W reprezentacji bazy Northwind zostało zastosowane połączenie obu podejść. Relacje pomiędzy dokumentami symulowane są zarówni poprzez zagnieżdżenie jak i referencje:
- **Referencje** - pozwalają ograniczyć redundancję niepotrzebnych danych przy każdym zwróconym zapytaniu. Dają również pewność, że nie zostanie przekroczony rozmiar dokumentu - 16Mb.
- **Zagnieżdżenie** - pozwala ograniczyć złożoność zapytań, często do jednego dokumentu.

Tabele łącznikowe takie jak: Order Details, Employee Territories oraz CustomerCustomerDemo nie zostały uwzględnione jako kolekcje w bazie danych.

## Plik konfiguracyjny bazy danych MongoDB 
Wspierany przez Spring Boot plik konfiguracyjny:

<img width="450" alt="Screenshot 2021-08-15 at 23 44 41" src="https://user-images.githubusercontent.com/34041060/129493705-194af92d-f823-4334-9ec0-bb02e05270eb.png">

- `spring.data.mongodb.authentication-database` – nazwa autentyfikacji bazy danych.
- `spring.data.mongodb.username` – nazwa użytkownika w serwerze MongoDB.
- `spring.data.mongodb.password` – hasło do konta użytkownika w serwerze MongoDB.
- `spring.data.mongodb.database` – nazwa bazy danych.
- `spring.data.mongodb.host` – nazwa hosta serwera MongoDB.
- `logging.level.org.springframework.data.mongodb.repository.query` – pozwala włączyć logi dotyczące wykonywanych zapytań na bazie danych.

## Konteneryzacja
Aplikacja zostala skonteneryzowana za pośrednictwem Dockera – wyróżnione zostały 2 kontenery:
- Kontener skonfigurowanej bazy MongoDB - `mongo`
- Kontener serwisu serwera - `northwind-service`

<img width="300" alt="Screen Shot 2021-08-16 at 00 35 05 AM" src="https://user-images.githubusercontent.com/34041060/129494676-5b738e5c-37e5-4dec-9f45-808291d83a8e.png">

**Budowanie kontenerów:**

`docker-compose up -d`

**Usunięcie kontenerów:**

`docker-compose down`

## Project Lombok:
Biblioteka Javy, która w znaczącym stopniu ułatwia definiowanie klas, szczególnie klas modelu, które powinny być zgodne ze standardem JavaBeans lub być klasami dla obiektów niemodyfikowalnych (immutable).

**Rezultat**: Znaczące skrócenie kodu poprzez zastąpienie wszystkich getter'ów i setter'ów adnotacjami @Getter oraz @Setter.

**Plugin do dodania do InteliJ:** https://plugins.jetbrains.com/plugin/6317-lombok.

## Swagger
Skonfigurowany w klasie SwaggerConfig, w wersji 3.0:

<img width="450" alt="Screen Shot 2021-08-16 at 00 40 35 AM" src="https://user-images.githubusercontent.com/34041060/129494798-7ec21a96-0105-4a89-9ee0-5eea783cf4d7.png">

**Link:**  http://localhost:8080/swagger-ui/index.html


 
