# Social Media Posts Mechanism

## Overview
This project demonstrates a simple social media posts mechanism built using Django and JavaScript. It dynamically loads and displays posts as the user scrolls down the page, creating an infinite scroll experience. The posts are fetched from the server in batches, ensuring smooth performance and scalability.

## Features
- **Infinite Scrolling:** Automatically loads new posts as the user reaches the bottom of the page.
- **Dynamic Content Loading:** Fetches posts in batches using AJAX calls to optimize performance.
- **Responsive Design:** Adjusts to different screen sizes and devices for a seamless user experience.

## Technologies Used
- **Backend:** Django
- **Frontend:** HTML, CSS, JavaScript
- **AJAX:** For fetching posts dynamically

## File Structure
```
project/
|-- templates/
|   |-- index.html  # Contains the main page layout
|
|-- static/
|   |-- css/
|   |   |-- styles.css  # Styles for the application
|   |-- js/
|   |   |-- script.js  # JavaScript logic for loading posts
|
|-- views.py         # Django views for serving posts
|-- urls.py          # URL routing for the application
|-- models.py        # Model definitions for posts
|-- serializers.py   # Serializers for converting model data to JSON
```

## How It Works
1. **Initial Load:**
   - When the page loads, the JavaScript function `load()` is triggered to fetch the first batch of posts from the server.
   - Posts are rendered dynamically using the `add_post()` function.

2. **Infinite Scrolling:**
   - An event listener is attached to the `window.onscroll` event. When the user scrolls to the bottom of the page, the `load()` function is triggered again.
   - The function calculates the range of posts to fetch (e.g., posts 1–20, 21–40, etc.) and sends an AJAX request to the server.

3. **Server-Side Logic:**
   - The Django server handles requests to the `/posts` endpoint. It fetches the requested range of posts from the database and returns them in JSON format.

4. **Frontend Rendering:**
   - The fetched posts are added to the DOM inside the `#posts` container.

## API Endpoint
### `/posts`
**Method:** GET

**Parameters:**
- `start`: The starting index of posts to fetch.
- `end`: The ending index of posts to fetch.

**Response:**
A JSON object containing the requested posts. For example:
```json
{
    "posts": [
        "Post content 1",
        "Post content 2",
        "Post content 3"
    ]
}
```

## Setup Instructions
1. **Clone the Repository:**
   ```
   git clone https://github.com/Jaweria-B/scrolling
   cd project
   ```

2. **Install Dependencies:**
   Ensure you have Python and Django installed. Install required packages:
   ```
   pip install -r requirements.txt
   ```

3. **Run Migrations:**
   ```
   python manage.py makemigrations
   python manage.py migrate
   ```

4. **Run the Development Server:**
   ```
   python manage.py runserver
   ```

5. **Access the Application:**
   Open your web browser and navigate to `http://127.0.0.1:8000/`.

## Future Enhancements
- Add user authentication to manage posts.
- Enable likes, comments, and shares for each post.
- Implement a database cache for faster data retrieval.
- Enhance the UI with additional styling and animations.

## Contributing
Feel free to fork this repository and submit pull requests. Suggestions and improvements are always welcome!

## License
This project is licensed under the MIT License. See the `LICENSE` file for details.

