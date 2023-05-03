<a name="readme-top"></a>

[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
  <h1 align="center">Census Toy API</h3>
  
<p align="center">
  <img src="https://user-images.githubusercontent.com/126913704/235832084-dce4819b-77a4-491d-a97c-952af4de70db.png" alt="My Image" width="500" height="auto">
</p>

  <p align="center">
    <br />
    <br />
    <br />
    <a href="https://github.com/Farangis88/Census_Toy_automation/issues">Report Bug</a>
    ·
    <a href="https://github.com/Farangis88/Census_Toy_automation/issues">Request Feature</a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-task">About The Task</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#requirements">Requirements</a>
      <ul>
        <li><a href="#steps">Steps</a></li>
      </ul>
    </li>
    <li><a href="#api-results">Census Toy API Test Results</a></li>
    <li><a href="#test-summary">Test Results Summary</a></li>
    <li><a href="#descr-bugs">Test Descriptions and Bugs</a></li>
  </ol>
</details>

<!-- ABOUT THE PROJECT -->

## About the Task

### Why Pytest Framework 

One of the primary reasons for my preference for the Pytest framework stems from its capability to deliver highly comprehensible and user-friendly reporting within the terminal. As an individual with extensive experience utilizing Pytest, I have consistently found its reporting format to be remarkably clear and easy to understand. Furthermore, Pytest has proven to be a dependable choice for both test reporting and code execution, especially in comparison to Javascript. The abundance of available libraries within the Pytest ecosystem has also played a crucial role in solidifying my decision to adopt this framework.

### How to replicate the tests

To replicate these tests, follow the requirements and steps below:

## Built With

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![PyCharm](https://img.shields.io/badge/pycharm-143?style=for-the-badge&logo=pycharm&logoColor=black&color=black&labelColor=green)
![Testing-Library](https://img.shields.io/badge/-TestingLibrary-%23E33332?style=for-the-badge&logo=testing-library&logoColor=white)
![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)
![Jira](https://img.shields.io/badge/jira-%230A0FFF.svg?style=for-the-badge&logo=jira&logoColor=white)

## Requirements

-   Python 3.6 or higher
-   Pytest library. You can install it using `pip install pytest`
-   Requests library. You can install it using `pip install requests`

## Steps

1.  Create a new Python file named test_census_toy_api.py.
2.  Copy the code provided above and paste it into the test_census_toy_api.py file.
3.  Ensure that the url variable points to the correct Census Toy API endpoint.
4.  Open a terminal or command prompt and navigate to the directory containing the test_census_toy_api.py file.
5.  Run the command pytest test_census_toy_api.py to execute the tests.
6.  Observe the test results displayed in the terminal or command prompt.

If the tests are successful, you should see a summary of the tests that have passed and failed. If any tests fail, you can check the AssertionError messages for details on what went wrong.


## Census Toy API Test Results

This README file contains descriptions of the tests conducted on the Census Toy API service, including what worked and what did not. Any bugs discovered during the testing process are formatted as if they were being reported in a new ticket.


## Test Results Summary


The following tests were conducted on the Census Toy API service:

- test_invalid_request_body: **PASSED**
- test_top_less_than_1: **FAILED**
- test_users_not_array: **FAILED**
- test_missing_required_field: **FAILED**
- test_top_parameter_with_invalid_action_type: **FAILED**
- test_top_not_integer: **FAILED**
- test_top_greater_than_number_of_countries: **FAILED**
- test_count_by_country_with_duplicates: **FAILED**
- test_count_by_gender_duplicates: **PASSED**


## Test Descriptions and Bugs


### Test: test_top_less_than_1

`Description:` This test checks if the API returns a 400 Bad Request status code when the "top" parameter is less than 1.

`Result:` FAILED

`Bug Report:`

- **Title:** API should return 400 Bad Request when "top" is less than 1
- **Description:** When sending a request with a "top" parameter less than 1, the API should return a 400 Bad Request status code. However, it currently returns a 200 OK status code.
- **Steps to reproduce:**
  1. Send a POST request to the API with a "top" parameter less than 1.
  2. Observe that the response status code is 200 instead of the expected 400.
- **Suggested fix:** Update the API to validate the "top" parameter and return a 400 status code when it is less than 1.

### Test: test_users_not_array

`Description:` This test checks if the API returns a 400 Bad Request status code when the "users" parameter is not an array.

`Result:` FAILED

`Bug Report:`

- **Title:** API should return 400 Bad Request when "users" is not an array
- **Description:** When sending a request with a "users" parameter that is not an array, the API should return a 400 Bad Request status code. However, it currently returns a 200 OK status code.
- **Steps to reproduce:**
  1. Send a POST request to the API with a "users" parameter that is not an array.
  2. Observe that the response status code is 200 instead of the expected 400.
- **Suggested fix:** Update the API to validate the "users" parameter and return a 400 status code when it is not an array.

### Test: test_missing_required_field

`Description:` This test checks if the API returns a 400 Bad Request status code when a required field is missing from the request.

`Result:` FAILED

`Bug Report:`

- **Title:** API should return 400 Bad Request when a required field is missing
- **Description:** When sending a request with a missing required field, the API should return a 400 Bad Request status code. However, it currently returns a 200 OK status code.
- **Steps to reproduce:**
  1. Send a POST request to the API with a missing required field.
  2. Observe that the response status code is 200 instead of the expected 400.
- **Suggested fix:** Update the API to validate required fields and return a 400 status code when a required field is missing.

### Test: test_top_parameter_with_invalid_action_type

Farrukh QA, [5/2/2023 7:53 PM]

`Description:` This test checks if the API returns a 400 Bad Request status code when the "top" parameter is used with an invalid action type.

`Result:` FAILED

`Bug Report:`

- **Title:** API should return 400 Bad Request when "top" is used with an invalid action type
- **Description:** When sending a request with a "top" parameter and an invalid action type, the API should return a 400 Bad Request status code. However, it currently returns a 200 OK status code.
- **Steps to reproduce:**
  1. Send a POST request to the API with a "top" parameter and an invalid action type.
  2. Observe that the response status code is 200 instead of the expected 400.
- **Suggested fix:** Update the API to validate the action type and return a 400 status code when the "top" parameter is used with an invalid action type.

### Test: test_top_not_integer

`Description:` This test checks if the API returns a 400 Bad Request status code when the "top" parameter is not an integer.

`Result:` FAILED

`Bug Report:`

- **Title:** API should return 400 Bad Request when "top" is not an integer
- **Description:** When sending a request with a "top" parameter that is not an integer, the API should return a 400 Bad Request status code. However, it currently returns a 200 OK status code.
- **Steps to reproduce:**
  1. Send a POST request to the API with a "top" parameter that is not an integer. 2. Observe that the response status code is 200 instead of the expected 400.

-   **Suggested fix:** Update the API to validate the "top" parameter and return a 400 status code when it is not an integer.

### Test: test_top_greater_than_number_of_countries

`Description:` This test checks if the API returns a 400 Bad Request status code when the "top" parameter is greater than the number of countries.

`Result:` FAILED

`Bug Report:`

-   **Title:** API should return 400 Bad Request when "top" is greater than the number of countries
-   **Description:** When sending a request with a "top" parameter that is greater than the number of countries, the API should return a 400 Bad Request status code. However, it currently returns a 200 OK status code.
-   **Steps to reproduce:**
    1.  Send a POST request to the API with a "top" parameter that is greater than the number of countries.
    2.  Observe that the response status code is 200 instead of the expected 400.
-   **Suggested fix:** Update the API to validate the "top" parameter and return a 400 status code when it is greater than the number of countries.

### Test: test_count_by_country_with_duplicates

`Description:` This test checks if the API correctly counts the number of users by country when there are duplicate countries in the input.

`Result:` FAILED

`Bug Report:`

-   **Title:** API should return correct count when there are duplicate countries
-   **Description:** When counting users by country with duplicate countries in the input, the API should return the correct counts for each country. However, the current response returns incorrect counts.
-   **Steps to reproduce:**
    1.  Send a POST request to the API with an actionType of "CountByCountry" and a list of users with duplicate countries.
    2.  Observe that the response returns incorrect counts for the countries.
-   **Suggested fix:** Update the API to correctly count users by country when there are duplicate countries in the input.


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://www.linkedin.com/in/farangiskarimova/
[product-screenshot]: ![starbucks](https://user-images.githubusercontent.com/22685770/235320606-cf6e5174-26f1-4a2e-97ec-a20b4daabc28.jpg)
