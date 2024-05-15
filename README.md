**##COVID-19 Data Analysis Project**

Introduction

This project analyzes COVID-19 data from the PortfolioProject database, focusing on various aspects such as deaths, vaccinations, and infection rates. The SQL queries provided here can be used to extract insights from the dataset.


Dataset

The dataset consists of two main tables: CovidDeaths and CovidVaccinations. The CovidDeaths table contains information about COVID-19 deaths, including location, date, total cases, new cases, total deaths, and population. The CovidVaccinations table contains data on COVID-19 vaccinations, including location, date, and new vaccinations.


Queries

Ordering CovidDeaths Data

SQL: SELECT * FROM PortfolioProject..CovidDeaths ORDER BY 3,4


Total Cases vs. Total Deaths

SQL: SELECT Location, Date, Total_Cases, Total_Deaths, (Total_Deaths/Total_Cases)*100 AS DeathPercentage FROM PortfolioProject..CovidDeaths WHERE Location LIKE '%states%' ORDER BY 1,2


Population Infected Percentage

SQL: SELECT Location, Date, Total_Cases, Population, (Total_Cases/Population)*100 AS PercentPopulationInfected FROM PortfolioProject..CovidDeaths WHERE Location LIKE '%states%' ORDER BY 1,2


Countries with Highest Infection Rate

SQL: SELECT Location, Population, MAX(Total_Cases) AS HighestInfectionCount, MAX((Total_Cases/Population))*100 AS PercentPopulationInfected FROM PortfolioProject..CovidDeaths GROUP BY Location, Population ORDER BY PercentPopulationInfected DESC


Countries with Highest Death Count

SQL: SELECT Location, MAX(CAST(Total_Deaths AS INT)) AS TotalDeathCount FROM PortfolioProject..CovidDeaths WHERE Continent IS NOT NULL GROUP BY Location ORDER BY TotalDeathCount DESC


Continents with Highest Death Count

SQL: SELECT Continent, MAX(CAST(Total_Deaths AS INT)) AS TotalDeathCount FROM PortfolioProject..CovidDeaths WHERE Continent IS NOT NULL GROUP BY Continent ORDER BY TotalDeathCount DESC


Global Numbers

SQL: SELECT Date, SUM(New_Cases) AS Total_Cases, SUM(CAST(New_Deaths AS INT)) AS Total_Deaths, SUM(CAST(New_Deaths AS INT))/SUM(New_Cases)*100 AS DeathPercentage FROM PortfolioProject..CovidDeaths WHERE Continent IS NOT NULL GROUP BY Date ORDER BY 1,2


Percentage of Population Vaccinated

SQL: SELECT *, (RollingPeopleVaccinated/Population)*100 FROM PopvsVac


Usage

Clone the repository.

Connect to the PortfolioProject database.

Run the SQL queries in your SQL client to analyze the data.

