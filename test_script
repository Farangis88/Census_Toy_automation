import pytest
import requests
import json

url = "https://census-toy.nceng.net/prod/toy-census"
# Test how API responds to the empty body
def test_api_response_empty_body():
    response = requests.post(url)
    assert response.status_code == 400  # Expecting a 400 Bad Request due to missing required fields


# Test if the API returns the correct response for CountByGender action type
def test_count_by_gender():
    data = {
        "actionType": "CountByGender",
        "users": [
            {"gender": "male"},
            {"gender": "female"},
            {"gender": "male"},
            {"gender": "other"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 200
    returning_data = response.json()
    assert {"name": "male", "value": 2} in returning_data
    assert {"name": "female", "value": 1} in returning_data
    assert {"name": "other", "value": 1} in returning_data

# Test if the API returns the correct response for CountByCountry action type
def test_count_by_country():
    data = {
        "actionType": "CountByCountry",
        "users": [
            {"nat": "US"},
            {"nat": "UK"},
            {"nat": "US"},
            {"nat": "CA"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 200
    result = response.json()
    assert {"name": "US", "value": 2} in result
    assert {"name": "UK", "value": 1} in result
    assert {"name": "CA", "value": 1} in result

# Test if the API returns the correct response for CountPasswordComplexity action type
def test_count_password_complexity():
    data = {
        "actionType": "CountPasswordComplexity",
        "users": [
            {"login": {"password": "abc123"}},
            {"login": {"password": "abc!@#"}},
            {"login": {"password": "123!@#"}}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 200
    result = response.json()
    assert {"name": "abc123", "value": 0} in result
    assert {"name": "abc!@#", "value": 3} in result
    assert {"name": "123!@#", "value": 3} in result

# Test if the API returns the correct response when the top parameter is used
def test_top_parameter():
    data = {
        "actionType": "CountByCountry",
        "top": 2,
        "users": [
            {"nat": "US"},
            {"nat": "UK"},
            {"nat": "US"},
            {"nat": "CA"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 200
    result = response.json()
    assert len(result) == 2
    assert {"name": "US", "value": 2} in result

# Test if the API returns an error for invalid inputs
def test_invalid_input():
    data = {
        "actionType": "InvalidActionType",
        "users": [
            {"gender": "male"},
            {"gender": "female"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 400  # Expecting a 400 Bad Request due to invalid action type

# Test that the API returns an error if the request body is not valid JSON.

def test_invalid_request_body():
    invalid_data = "invalid json data"
    response = requests.post(url, data=invalid_data)
    assert response.status_code == 400

# Test that the API returns an error if the top parameter is less than 1.

def test_top_less_than_1():
    data = {"actionType": "get_top_users", "top": 0}
    response = requests.post(url, json=data)
    assert response.status_code == 400

#Test that the API returns an error if the users field is not an array.

def test_users_not_array():
    data = {"actionType": "CountByCountry", "users": "Invalid users data"}
    response = requests.post(url, json=data)
    assert response.status_code == 400




# Test that the API returns an error if a user is missing a required field.
def test_missing_required_field():
    data = {
        "actionType": "CountByCountry",
        "users": [
            {"name": "Alice", "country": "USA"},
            {"name": "Bob", "age": 25},
            {"name": "Charlie", "country": "Canada", "age": 30},
        ]
     }
    response = requests.post(url, json=data)
    assert response.status_code == 400


 # Test that the API returns an error if the top parameter is used with CountByGender or CountPasswordComplexity.

def test_top_parameter_with_invalid_action_type():
    data = {"actionType": "CountByGender", "top": 10}
    response = requests.post(url, json=data)
    assert response.status_code == 400

    data = {"actionType": "CountPasswordComplexity", "users": [], "top": 5}
    response = requests.post(url, json=data)
    assert response.status_code == 400


# Test that the API returns an error if the top parameter is not an integer.

def test_top_not_integer():
    data = {"actionType": "get_top_users", "top": "invalid_top"}
    response = requests.post(url, json=data)
    assert response.status_code == 400

# Test that the API returns an error if the top parameter is greater than the number of countries in the user data.

def test_top_greater_than_number_of_countries():
    data = {
        "actionType": "CountByCountry",
        "top": 10,
        "users": [
            {"id": 1, "country": "USA", "gender": "M"},
            {"id": 2, "country": "USA", "gender": "F"},
            {"id": 3, "country": "Canada", "gender": "M"},
            {"id": 4, "country": "Canada", "gender": "F"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 400



# Test that the API returns the correct count of users when the users field contains multiple users with the same nationality.

def test_count_by_country_with_duplicates():
    data = {
        "actionType": "CountByCountry",
        "users": [
            {"name": "John Doe", "nationality": "USA"},
            {"name": "Jane Doe", "nationality": "USA"},
            {"name": "Bob Smith", "nationality": "UK"},
            {"name": "Alice Brown", "nationality": "UK"},
            {"name": "Charlie Lee", "nationality": "China"},
            {"name": "Lily Chen", "nationality": "China"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 200
    result = response.json()
    assert {"name": "USA", "value": 2} in result
    assert {"name": "UK", "value": 2} in result
    assert {"name": "China", "value": 2} in result


# Test that the API returns the correct count of users when the users field contains multiple users with the same gender.

def test_count_by_gender_duplicates():
    data = {
        "actionType": "CountByGender",
        "users": [
            {"gender": "male"},
            {"gender": "female"},
            {"gender": "male"},
            {"gender": "male"}
        ]
    }
    response = requests.post(url, json=data)
    assert response.status_code == 200
    result = response.json()
    assert {"name": "male", "value": 3} in result
    assert {"name": "female", "value": 1} in result
