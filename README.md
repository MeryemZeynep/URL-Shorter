# URL Shortener

This is a simple URL shortener web application built using Flask, a Python web framework. The application generates short URLs for long URLs provided by users and redirects users to the original long URL when they visit the shortened URL.

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/your-username/url-shortener.git
   ```

2. Navigate to the project directory:

   ```bash
   cd url-shortener
   ```

3. Install the required dependencies:

   ```bash
   pip install flask
   ```

## Usage

1. Run the Flask application:

   ```bash
   python app.py
   ```

2. Open a web browser and visit `http://localhost:5000` to access the URL shortener.

3. Enter a long URL in the provided input field and click the "Shorten" button.

4. The application will generate a unique short URL for the entered long URL.

5. Copy the shortened URL and share it with others.

6. When someone visits the shortened URL, they will be redirected to the original long URL.

## How It Works

The URL shortener uses the Flask web framework to handle HTTP requests and render HTML templates. Here's an overview of how the application works:

1. The `index()` function serves as the view for the home page (`/`). It handles both GET and POST requests.

2. If the user submits a POST request by entering a long URL, the `index()` function generates a short URL using the `generate_short_url()` function. It checks if the generated short URL already exists in the `shortened_urls` dictionary and generates a new one if necessary.

3. The long URL and its corresponding short URL are stored in the `shortened_urls` dictionary.

4. The `index()` function returns the shortened URL to the user.

5. When a user visits a shortened URL (e.g., `/abc123`), the `redirect_url()` function is triggered.

6. The `redirect_url()` function looks up the long URL associated with the short URL in the `shortened_urls` dictionary.

7. If the long URL is found, the function redirects the user to the original URL.

8. If the long URL is not found, a "URL not found" message with a 404 status code is returned.

## Template

The HTML template (`index.html`) used for the home page is a simple form with an input field and a submit button. Here's a brief explanation of the template structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>URL Shortener</title>
</head>
<body>
    <h1>URL SHORTENER</h1>
    <form method="POST" action="{{ url_for('index') }}">
        <input type="text" name="long_url" placeholder="Enter the long URL">
        <button type="submit">Shorten</button>
    </form>
</body>
</html>
```

The form's `action` attribute is set to `{{ url_for('index') }}`, which ensures that the form data is submitted to the `index()` function in the Flask application.

## Notes

- The `generate_short_url()` function generates a short URL using a combination of uppercase letters, lowercase letters, and digits. The default length of the short URL is 6 characters, but it can be customized by providing a different value for the `length` parameter.

- The `shortened_urls` dictionary serves as a simple in-memory storage for mapping short URLs to long URLs. Keep in mind that this implementation is not suitable for production use and may lose

 data when the server restarts.

- The application runs in debug mode (`debug=True`) to enable error messages and auto-reloading of code changes during development. You may want to disable debug mode in a production environment.

- This readme assumes you have a basic understanding of Python, Flask, and HTML. If you are new to Flask, consider checking out the Flask documentation for more information.

That's it! You now have a basic understanding of how to use and modify this URL shortener application. Feel free to customize and improve it according to your needs.