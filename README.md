# Northwind database - MongoDB

## Spis treści
1. [Opis](#opis)
2. [Symulacja relacji w dokumentowej bazie danych](#symulacja-relacji-w-dokumentowej-bazie-danych)
3. [Technologie](#technologie)
 - [Swagger](#swagger)
 - [Project Lombok](#project-lombok)
4. [Konfiguracja bazy danych MongoDB](#konfiguracja-bazy-danych-mongodb)
5. [Konteneryzacja](#konteneryzacja)

## Opis
Celem projektu było zaimplementowanie systemu realizującego wybrane, podstawowe operacje na przykładowej bazie Northwind, w wybranej technologii.

<img width="450" alt="Schemat" src="https://user-images.githubusercontent.com/34041060/129492965-a82a59f0-1ac1-4239-a86e-fd1f3c32f29c.png">

## Symulacja relacji w dokumentowej bazie danych
- **Embedded way** - jeden dokument zostaje osadzony w innym dokumencie.
- **Reference approach** - dokumenty przechowywane są oddzielnie, ale jeden dokument zawiera odniesienie do pola id drugiego dokumentu.

W reprezentacji bazy Northwind zostało zastosowane połączenie obu podejść. Relacje pomiędzy dokumentami symulowane są zarówni poprzez zagnieżdżenie jak i referencje:
- **Referencje** - pozwalają ograniczyć redundancję niepotrzebnych danych przy każdym zwróconym zapytaniu. Dają również pewność, że nie zostanie przekroczony rozmiar dokumentu - 16Mb.
- **Zagnieżdżenie** - pozwala ograniczyć złożoność zapytań, często do jednego dokumentu.

Tabele łącznikowe takie jak: Order Details, Employee Territories oraz CustomerCustomerDemo nie zostały uwzględnione jako kolekcje w bazie danych.

## Technologie
- **MongoDB** – nierelacyjny system do zarządzania bazą danych Northwind
- **Spring Boot + Java11** – serwis realizujący podstawowe operacje na bazie Northwind.
- **Swagger** – automatyczna dokumentacja metod RestAPI.
- **Docker** – konteneryzacja aplikacji.

### Swagger
Zależności z pliku pom.xml (wersja 3.0):

<img width="300" alt="Screen Shot 2021-08-23 at 00 56 12 AM" src="https://user-images.githubusercontent.com/34041060/130372643-b7ebaec0-5fd8-45b7-8904-d0554adade24.png">

Skonfigurowany w klasie SwaggerConfig:

<img width="450" alt="Screen Shot 2021-08-16 at 00 40 35 AM" src="https://user-images.githubusercontent.com/34041060/129494798-7ec21a96-0105-4a89-9ee0-5eea783cf4d7.png">

### Project Lombok
Biblioteka Javy, która w znaczącym stopniu ułatwia definiowanie klas. Znacząco skraca kod poprzez zastąpienie getterów, setterów, czy konstruktorów za pomocą adnotacji.

Zależności z pliku pom.xml:

<img width="250" alt="Screen Shot 2021-08-23 at 00 55 47 AM" src="https://user-images.githubusercontent.com/34041060/130372630-4725e7a6-ed2e-406e-9798-117f4c284660.png">

## Konfiguracja bazy danych MongoDB
Zależność z pliku pom.xml:

<img width="350" alt="Screenshot 2021-08-24 at 00 45 21" src="https://user-images.githubusercontent.com/34041060/130528918-2db761f6-c156-46c2-a4bf-005c9aefa441.png">


Wspierany przez Spring Boot plik konfiguracyjny application.properties:

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

`docker-compose up -d` - budowanie kontenerów.

`docker-compose down` - usunięcie kontenerów.

## Adres
- http://localhost:8080
- **Swagger:** http://localhost:8080/swagger-ui/index.html

## Dokumentacja
- [Opis systemu](https://github.com/igordzie97/mongodb-databases-project/blob/main/documentation/documentation.pdf)

## Autorzy:
- Igor Dzierwa
- Adrian Nędza
- Konrad Makuch
