# ScreenMatch 🎬

ScreenMatch is a Java application that consumes the **OMDb API** to retrieve information about TV series, seasons, and episodes.  
The project demonstrates modern Java features such as **Streams, Lambdas, Optional, and data processing with statistics** using the **Spring Boot framework**.

This project was developed as part of the course **"Java: Working with Lambdas, Streams and Spring Framework"**.

---

## 📌 Features

The application allows users to:

- 🔎 Search for a TV series by name
- 📺 Retrieve all seasons and episodes of a series
- ⭐ Display the **Top 5 highest rated episodes**
- 📅 Filter episodes released after a specific year
- 🔍 Search for episodes by **title fragment**
- 📊 Calculate **average ratings per season**
- 📈 Generate statistics such as:
  - Average rating
  - Best rated episode
  - Worst rated episode
  - Total number of evaluated episodes

---

## 🛠 Technologies Used

- **Java 17+**
- **Spring Boot**
- **Jackson** (JSON parsing)
- **Java Streams API**
- **Lambdas**
- **Optional**
- **OMDb API**

---

## 📂 Project Structure
````
screenmatch
│
├── model
│   ├── DatosSerie.java
│   ├── DatosTemporada.java
│   ├── DatosEpisodio.java
│   └── Episodio.java
│
├── service
│   ├── ConsumoAPI.java
│   ├── ConvierteDatos.java
│   └── IConvierteDatos.java
│
├── principal
│   └── Principal.java
│
└── ScreenmatchApplication.java
````
### Description

| Package | Purpose |
|------|------|
| `model` | Classes and records representing series, seasons, and episodes |
| `service` | API consumption and JSON data conversion |
| `principal` | Application logic and user interaction |
| `ScreenmatchApplication` | Spring Boot entry point |

---

## 🚀 How to Run the Project

### 1️⃣ Clone the repository

```bash
git clone https://github.com/GuillenA7/screenmatch-spring.git
cd screenmatch
````

### 2️⃣ Open the project

You can open it with:

* IntelliJ IDEA
* Eclipse
* VS Code (Java extension)

### 3️⃣ Run the application

Run the main class:

```
ScreenmatchApplication.java
```

The application will start in the terminal.

---

## 💻 Example Usage

When running the program, you will see:

```
Enter the name of the series you want to search:
```

Example input:

```
Game of Thrones
```

The application will:

* Fetch data from OMDb API
* Display seasons and episodes
* Show statistics and rankings

Example output:

```
Top 5 Episodes
Season 6 - Battle of the Bastards (9.9)
Season 6 - The Winds of Winter (9.9)

Average rating: 8.72
Best episode rating: 9.9
Worst episode rating: 4.0
Total evaluated episodes: 68
```

---

## 📊 Stream Processing Examples

The project uses Java Streams to process data efficiently.

Example: Average rating per season

```java
Map<Integer, Double> ratingsBySeason = episodios.stream()
    .filter(e -> e.getEvaluacion() > 0)
    .collect(Collectors.groupingBy(
        Episodio::getTemporada,
        Collectors.averagingDouble(Episodio::getEvaluacion)
    ));
```

Example: Statistics generation

```java
DoubleSummaryStatistics stats = episodios.stream()
    .filter(e -> e.getEvaluacion() > 0)
    .collect(Collectors.summarizingDouble(Episodio::getEvaluacion));
```

---

## 🌐 API Used

This project uses the **OMDb API** to retrieve information about movies and TV series.

Website:

```
https://www.omdbapi.com/
```

Example request:

```
https://www.omdbapi.com/?t=game+of+thrones&apikey=YOUR_API_KEY
```

---

## 🎯 Learning Objectives

This project demonstrates:

* Functional programming with **Java Streams**
* Use of **Lambda expressions**
* JSON mapping with **Jackson**
* Safe handling of values using **Optional**
* Data aggregation and statistics generation
* API consumption in Java

---

## 📚 Course Reference

This project was developed while following the course:

**Java: Working with Lambdas, Streams and Spring Framework**

by **Alura Latam**.

---

## 👨‍💻 Author

Developed by **Adrian Guillen**

If you liked this project, feel free to ⭐ the repository!
