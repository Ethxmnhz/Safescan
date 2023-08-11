# Safescan

ACCESS THE LIVE WEBSITE HERE : https://ethxmnhz.github.io/Safescan/



**1. Set Up Your Development Environment:**

Make sure you have Python installed on your system. You can check by running `python --version` in your command prompt or terminal. If not installed, you can download it from the official Python website.

**2. Create a New Project:**

Create a new directory for your project and navigate to it in your terminal:


mkdir malware_scan_website
cd malware_scan_website


**3. Install Flask:**

Install Flask using `pip`, the Python package installer:
pip install flask



**4. Create the Backend:**



Create a file named app.py in your project directory. This file will contain the backend code for your website.




app.py:



    
<pre>'from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/upload', methods=['POST'])
def upload_file():
    uploaded_file = request.files['file']
    
    Implement file handling and scanning logic here
    Call your malware scanning API or library
    
    Example: Assume the file is clean
    result = 'File is clean.'
    
    return result
if __name__ == '__main__':
    app.run(debug=True)'
</pre>







    

**5. Create the Templates Folder:**

Create a folder named templates in your project directory. Inside the templates folder, create a file named index.html with the following content:


templates/index.html:



<pre>
```

<!--<!DOCTYPE htm>
<html>
<head>
    <title>Malware Scanning Website</title>
</head>
<body>
    <header>
        <h1>Malware Scanning Website</h1>
    </header>
    <main>
        <form action="/upload" method="POST" enctype="multipart/form-data">
            <input type="file" name="file" accept=".exe,.doc,.pdf" required>
            <button type="submit">Upload</button>
        </form>
        <div id="result-display">{{ result }}</div>
    </main>
    <footer>
        <p>&copy; 2023 MalwareScanApp</p>
    </footer>
</body>   CODE LOAD NAHI HORA FILE ME JAKE LO
</htm>-->
CODE LOAD NAHI HORA FILE ME JAKE LO
```
</pre>







File structure shoud be

malware_scan_website/
    app.py
    templates/
        index.html
    static/
        styles.css




**6. Run the Application:**

In your terminal, run the Flask application:


python app.py


Your website will be accessible at `http://127.0.0.1:5000/`. You'll be able to upload files, but remember that the scanning logic is not implemented in this example.

In the next step, we'll integrate a malware scanning API to handle the scanning process and display the results.







explanation 






**1. Setting Up the Backend:**

In the backend, we're using Python and the Flask framework. Flask allows us to create web applications easily.

**2. Creating the Backend Code (app.py):**

python

<pre>
```python
# Import necessary modules
from flask import Flask, render_template, request

# Create an instance of the Flask app
app = Flask(__name__)

# Route for the homepage
@app.route('/')
def index():
    return render_template('index.html')

# Route to handle file upload and scanning
@app.route('/upload', methods=['POST'])
def upload_file():
    uploaded_file = request.files['file']
    
    # Implement file handling and scanning logic here
    # Call your malware scanning API or library
    
    # Example: Assume the file is clean
    result = 'File is clean.'
    
    return result

# Run the app when this script is executed
if __name__ == '__main__':
    app.run(debug=True)
```
</pre>

**3. Understanding the Code:**

- We import necessary modules: `Flask` from the `flask` package and other components.
- We create an instance of the Flask app using `app = Flask(__name__)`.
- We define a route using `@app.route('/')` to handle the homepage. When a user accesses the root URL ("/"), the `index()` function is called. This function renders the `index.html` template.
- We define a route using `@app.route('/upload', methods=['POST'])` to handle file uploads. When a user submits the file upload form, the `upload_file()` function is called. It receives the uploaded file as part of the request (`request.files['file']`).
- Inside the `upload_file()` function, we would typically implement the logic to handle the uploaded file, such as sending it for scanning using an API or a scanning library. For now, we're assuming the file is clean and returning a simple result message.
- The `if __name__ == '__main__':` block ensures that the Flask app runs only when this script is directly executed, not when imported as a module.

**4. Running the Application:**

- Open a terminal and navigate to your project directory containing `app.py`.
- Run the Flask app by executing `python app.py`.
- Access the website at `http://127.0.0.1:5000/` in your web browser.
- You'll see the file upload form. You can upload a file, and upon submission, the result will be displayed (in this example, it's a static "File is clean." message).


how the aap.py got connected and working with the web files(html,css,js)?


Certainly! The `app.py` file (the backend) and the web files (HTML, CSS, and potentially JavaScript) work together to create a functional website. Let's break down how they are connected and how the communication flows:

**1. Flask App Setup:**

In the `app.py` file, you set up a Flask web application using the Flask framework. This application handles incoming requests and responds with appropriate content.
<pre>
```python
from flask import Flask, render_template, request

app = Flask(__name__)
```
</pre>

Here, you import the necessary components from the `flask` package and create an instance of the Flask app named `app`.

**2. Routing: Connecting URLs to Functions:**

Flask uses routes to map URLs to Python functions. When a user accesses a specific URL, the corresponding function is executed. For example:

```python
@app.route('/')
def index():
    return render_template('index.html')
```

In this code, when a user accesses the root URL ("/"), the `index()` function is executed. The `render_template()` function sends the content of the `index.html` template file as the response.

**3. Rendering HTML Templates:**

Flask uses templates to generate dynamic HTML content. Templates are HTML files with placeholders that can be filled in with data. In your `index.html` file, you have placeholders like `{{ result }}`.

```html
<div id="result-display">{{ result }}</div>
```

When the `render_template()` function is called, Flask replaces these placeholders with actual values and returns the complete HTML content to the browser.

**4. Static Files (CSS, JS):**

Static files like CSS and JavaScript enhance the visual and interactive aspects of your website. These files don't change dynamically like templates. Flask serves static files from the `static` folder.

To include CSS in your HTML, you use a link tag with the `href` attribute pointing to the CSS file:

```html
<link rel="stylesheet" href="{{ url_for('static', filename='styles.css') }}">
```

Here, `url_for('static', filename='styles.css')` generates a URL to the `styles.css` file in the `static` folder.

**5. User Interactions:**

When a user interacts with the website (e.g., uploads a file), the frontend (HTML and possibly JavaScript) sends a request to the backend (Flask app).

In the `app.py` file, you define routes to handle these requests. For instance, the `/upload` route is defined to handle file upload requests:
<pre>
```python
@app.route('/upload', methods=['POST'])
def upload_file():
    uploaded_file = request.files['file']
    
    # Implement file handling and scanning logic here
    
    result = 'File is clean.'
    
    return result
```

When a user submits the file upload form, a POST request is sent to the `/upload` route. The `upload_file()` function is executed, and you handle the file and implement the scanning logic.

**6. Responses to the Browser:**

The result of the function (e.g., a scanned file result) is returned as a response. In your example, the `result` message is sent back and displayed on the website.

**7. Running the Flask App:**

When you run the Flask app using `python app.py`, the app starts listening for incoming requests. When a user accesses the URLs defined in your routes (e.g., `/`, `/upload`), Flask routes the request to the appropriate function, executes the code, and sends a response back to the browser.

In essence, the Flask app manages the communication between the user's browser and the server, handling incoming requests and generating appropriate responses based on the defined routes and functions.







Process
|
|
|
|



Uploading files to a cloud storage service and then scanning them for malware involves a multi-step process that includes interacting with a cloud storage API and an antivirus API. Here's a general outline of the steps you would take:

1. Choose a Cloud Storage Provider:

Select a cloud storage provider that offers an API for programmatically uploading and managing files. Popular options include Amazon S3, Google Cloud Storage, Microsoft Azure Blob Storage, and Dropbox.

2. Obtain API Credentials:

Sign up for an account with the chosen cloud storage provider and obtain API credentials (such as API keys or tokens) that will allow your application to access their services.

3. Upload the File to Cloud Storage:

When a user uploads a file on your website, instead of handling the file directly, you'll upload it to the cloud storage service using their API. The API documentation will provide instructions on how to upload files.

4. Implement Malware Scanning:

After uploading the file to cloud storage, you'll need to initiate the malware scanning process. This might involve using an antivirus API or an external service like VirusTotal.

5. Scanning with Antivirus API:

Integrate an antivirus API into your application. These APIs allow you to send files for scanning and receive reports on their status. Popular options include ClamAV, VirusTotal, and MetaDefender. You'll need to sign up for an API key and follow their documentation for integrating the API into your application.

6. File Retrieval and Scanning:

Retrieve the file from the cloud storage using the API. Then, send the file to the antivirus API for scanning. The API will return a report indicating whether the file is clean or contains malware.

7. Display Scanning Result:

Once you receive the scanning result from the antivirus API, you can update your website's user interface to display the result to the user. For instance, you can inform the user whether the file is safe or not.

8. Delete or Quarantine Infected Files:

If a file is found to be infected, you should have a mechanism to handle it appropriately. This might involve quarantining the file, notifying the user, or automatically deleting the file.

9. User Notifications:

Notify the user of the scan result through your website's user interface or via email, depending on your design.



PENDING STEP 4



Here's how you can integrate the VirusTotal API into your `app.py`:

**1. Install Required Libraries:**

Install the `requests` library, which will help you make HTTP requests to the VirusTotal API. You can install it using:

```bash
pip install requests
```

**2. Update the `upload_file()` Function:**

```python
import requests

VIRUSTOTAL_API_KEY = 'YOUR_VIRUSTOTAL_API_KEY'

@app.route('/upload', methods=['POST'])
def upload_file():
    uploaded_file = request.files['file']
    
    # Save the uploaded file temporarily or directly upload to cloud storage

    # Implement VirusTotal API scanning
    scan_result = scan_file_with_virustotal(uploaded_file)

    return scan_result

def scan_file_with_virustotal(file):
    url = 'https://www.virustotal.com/api/v3/files'
    headers = {
        'x-apikey': VIRUSTOTAL_API_KEY
    }
    files = {'file': (file.filename, file.stream)}
    
    response = requests.post(url, headers=headers, files=files)
    json_response = response.json()
    
    if 'data' in json_response:
        scan_result = json_response['data']['attributes']['last_analysis_stats']
        result_message = f"Scan Results: {scan_result['malicious']} malicious, {scan_result['suspicious']} suspicious, {scan_result['undetected']} undetected."
        return result_message
    else:
        return "Scan failed."

if __name__ == '__main__':
    app.run(debug=True)
```

Replace `'YOUR_VIRUSTOTAL_API_KEY'` with your actual VirusTotal API key.

**3. Explanation:**

- We've added the VirusTotal API key as a constant at the top of the script.
- The `scan_file_with_virustotal()` function sends the uploaded file to the VirusTotal API for scanning. It returns the scan results, including the number of malicious, suspicious, and undetected results.
- The `upload_file()` function now calls `scan_file_with_virustotal()` to perform the scanning and returns the scan results.






Full Explanation



Certainly! Let's break down the code for implementing malware scanning using the VirusTotal API step by step:

**1. Import Required Libraries:**

```python
import requests
```

Here, we're importing the `requests` library, which will help us make HTTP requests to the VirusTotal API.

**2. Set Up Your VirusTotal API Key:**

```python
VIRUSTOTAL_API_KEY = 'YOUR_VIRUSTOTAL_API_KEY'
```

Replace `'YOUR_VIRUSTOTAL_API_KEY'` with the actual API key you obtained from your VirusTotal account.

**3. Define the `scan_file_with_virustotal()` Function:**

```python
def scan_file_with_virustotal(file):
    url = 'https://www.virustotal.com/api/v3/files'
    headers = {
        'x-apikey': VIRUSTOTAL_API_KEY
    }
    files = {'file': (file.filename, file.stream)}
    
    response = requests.post(url, headers=headers, files=files)
    json_response = response.json()
    
    if 'data' in json_response:
        scan_result = json_response['data']['attributes']['last_analysis_stats']
        result_message = f"Scan Results: {scan_result['malicious']} malicious, {scan_result['suspicious']} suspicious, {scan_result['undetected']} undetected."
        return result_message
    else:
        return "Scan failed."
```

This function takes an uploaded file as input, sends it to the VirusTotal API for scanning, and returns the scan results. It does the following:

- Constructs the API URL and headers.
- Prepares the file to be sent as part of the request.
- Makes a POST request to the VirusTotal API.
- Parses the JSON response and extracts the scan results.
- Returns a formatted message with the scan results.

**4. Update the `upload_file()` Function:**

```python
@app.route('/upload', methods=['POST'])
def upload_file():
    uploaded_file = request.files['file']
    
    # Save the uploaded file temporarily or directly upload to cloud storage

    # Implement VirusTotal API scanning
    scan_result = scan_file_with_virustotal(uploaded_file)

    return scan_result
```

In the `upload_file()` function:

- The uploaded file is obtained from the request.
- The `scan_file_with_virustotal()` function is called to scan the file using the VirusTotal API.
- The scan results are returned and displayed on the website.

**5. Running the Application:**

```python
if __name__ == '__main__':
    app.run(debug=True)
```

This code ensures that the Flask app runs only when this script is directly executed, not when imported as a module.




