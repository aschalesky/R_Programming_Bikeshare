# Bike Share Data Exploration Project

## Overview

This project explores bike share data from three major cities: Washington D.C., Chicago, and New York City. The goal is to analyze the data and answer questions related to user behavior, trip durations, and demographics. This Readme provides a guide to understanding and running the code associated with this project.

## Project Structure

The project consists of a single R Notebook (`.txt` file) that contains the code and markdown for analysis and visualization.

## Files
*   **paste.txt:** R Notebook containing all code, analysis, and visualizations.

## Dependencies

Before running the code, ensure you have the following R packages installed:

*   `ggplot2`
*   `lubridate`

You can install these packages using the following commands in R:


## Data Sources

The project uses data from bike share programs in three cities. While the provided code reads CSV files directly (named `new_york_city.csv`, `washington.csv`, and `chicago.csv`), these files are not included in the file.

To execute the code, you will need to obtain the data files and place them in the same directory as the R Notebook, or modify the `read.csv()` calls to point to the correct file paths.
**Note:** Since the data files weren't provided, you can find similar datasets online via the following resources:

*   **New York City:** Citi Bike Data
*   **Chicago:** Divvy Bicycle Sharing Data
*   **Washington D.C.:** Capital Bikeshare System Data

## Execution

1.  **Open the R Notebook:** Open the provided `paste.txt` file in RStudio or another compatible environment.
2.  **Set Working Directory (Optional):** If the data files are not in the same directory as the notebook, set the working directory to the location of the CSV files using the `setwd()` function.
3.  **Run the Code:** Execute the code cells sequentially within the notebook. The notebook is structured to guide you through the analysis process.

## Analysis and Questions Addressed

The notebook aims to answer the following questions using the bike share data:

1.  **What is the average travel time for users in different cities?**
    *   The code calculates and visualizes the average trip duration for each city using `ggplot2`.
2.  **What are the counts of each gender (only available for NYC and Chicago)?**
    *   The code analyzes and visualizes the distribution of genders in the New York City and Chicago datasets.
3.  **What is the most common month?**
    *   The code extracts the month from the `Start.Time` variable and determines the most frequent month for bike rentals.

## Key Code Snippets

*   **Importing Libraries:**
    ```
    library(ggplot2)
    library(lubridate) # To extract month from date
    ```
*   **Loading Data:**
    ```
    ny = read.csv('new_york_city.csv')
    wash = read.csv('washington.csv')
    chi = read.csv('chicago.csv')
    ```
*   **Data Cleaning:**
    ```
    wash$Gender <- NA
    wash$Birth.Year <- NA

    ny$City <- 'New York City'
    wash$City <- 'Washington'
    chi$City <- 'Chicago'
    ```
*   **Concatenating Dataframes:**
    ```
    concatenation <- function(d1, d2) {
      return(rbind(d1, d2))
    }
    ```
*   **Visualizing Data:**
    ```
    ggplot(aes(x = City, y = Trip.Duration), data = city) +
        geom_bar(position = 'dodge', stat = "summary", fun.y = "mean", fill = "blue", colour="black") +
        ggtitle('Average Trip Duration Across Cities') +
        labs(y = 'Average Trip Duration', x = 'City') +
        coord_flip()
    ```

## Interpretation of Results
The project provides insights into:

*   Trip duration differences across cities.
*   Gender distribution of bike share users in Chicago and New York City.
*   The most popular months for bike rentals.

The markdown sections within the notebook offer interpretations of these results.

## Notes

*   The notebook assumes that the data files are in the same directory as the script. You may need to adjust the file paths accordingly.
*   The Washington D.C. dataset lacks 'Gender' and 'Birth.Year' columns. The script handles this by adding `NA` values to these columns when combining the datasets.
