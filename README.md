<html>
   <head>
       <title>Sample HTML Code</title>
   </head>
   <body>
       
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cicada Programming Services</title>
    <link rel="stylesheet" href="styles.css">


    <header>
        <h1 class="decorative-title">ENOURI Programming Services</h1>
        <nav>
            <ul>
                <li><a href="#">Home</a></li>
                <li><a href="#">Services</a></li>
                <li><a href="#">About</a></li>
                <li><a href="#">Contact Us</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <section>
            <h2>Our Services</h2>
            <div class="service">
                <img ="web-development.jpg" alt="Web Development">
                <h3>Web Development</h3>
                <p>Professional website development tailored to your needs.</p>
                <p>Price: $500</p>
            </div>
            <div class="service">
                <img src="mobile-app.jpg" alt="Mobile App Development">
                <h3>Mobile App Development</h3>
                <p>Build modern mobile applications for iOS and Android.</p>
                <p>Price: $700</p>
            </div>
            <div class="service">
                <img src="system-design.jpg" alt="System Design">
                <h3>System Design</h3>
                <p>Custom system design for your business.</p>
                <p>Price: $1000</p>
            </div>
        </section>
        <section>
            <h2>Request Your Service Now</h2>
            <form action="/submit" method="POST" class="service-form">
                <div class="form-group">
                    <label for="name">Name:</label>
                    <input type="text" id="name" name="name" required>
                </div>
                <div class="form-group">
                    <label for="email">Email:</label>
                    <input type="email" id="email" name="email" required>
                </div>
                <div class="form-group">
                    <label for="service">Select Service:</label>
                    <select id="service" name="service">
                        <option value="web">Web Development</option>
                        <option value="mobile">Mobile App Development</option>
                        <option value="system">System Design</option>
                    </select>
                </div>
                <button type="submit">Submit</button>
            </form>
        </section>
    </main>
    <footer>
        <p>&copy; 2024 ENOURI Programming Services. All rights reserved.</p>
    </footer>
</body>
</html>
       
      


<!-- CSS codes -->
<style>
html {
body {
background: linear-gradient(to right, dodgerblue 0%, deepskyblue 100%);
    color: #333;
}

.decorative-title {
    font-family: 'Times New Roman', serif;
    font-size: 2.5em;
    color: #333;
    text-shadow: 2px 2px #ccc;
}

header {
    background-color: #333;
    color: #fff;
    padding: 10px 0;
    text-align: center;
}

nav ul {
    list-style: none;
    padding: 0;
}

nav ul li {
    display: inline;
    margin: 0 10px;
}

nav ul li a {
    color: #fff;
    text-decoration: none;
}

.service {
    border: 1px solid #ccc;
    padding: 10px;
    margin: 20px 0;
    background-color: #fff;
    text-align: center;
}

.service img {
    max-width: 100%;
    height: auto;
}

.service-form {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    background-color: #fff;
    border: 1px solid #ccc;
    border-radius: 5px;
}

.form-group {
    display: flex;
    flex-direction: column;
    margin-bottom: 15px;
}

.form-group label {
    margin-bottom: 5px;
    font-weight: bold;
}

.form-group input,
.form-group select {
    padding: 8px;
    font-size: 1em;
    border: 1px solid #ccc;
    border-radius: 4px;
}

button {
    padding: 10px;
    font-size: 1em;
    color: #fff;
    background-color: #333;
    border: none;
    cursor: pointer;
    border-radius: 4px;
}

button:hover {
    background-color: #555;
}

footer {
    text-align: center;
    padding: 10px;
    background-color: #333;
    color: #fff;
    margin-top: 20px;
}
}
h1{
   color: white;
}

</style>

<!-- c++ codes -->


<script>
#include <iostream>
#include <httplib.h>
#include <fstream>
#include <string>

// دالة لقراءة الملفات (HTML وCSS)
std::string readFile(const std::string& filename) {
    std::ifstream file(filename);
    if (!file.is_open()) {
        return "File not found!";
    }
    std::string content((std::istreambuf_iterator<char>(file)), std::istreambuf_iterator<char>());
    file.close();
    return content;
}

int main() {
    httplib::Server svr;

    // إرسال صفحة HTML عند زيارة /
    svr.Get("/", [](const httplib::Request&, httplib::Response& res) {
        std::string html_content = readFile("index.html");
        res.set_content(html_content, "text/html");
    });

    // إرسال CSS عند زيارة /styles.css
    svr.Get("/styles.css", [](const httplib::Request&, httplib::Response& res) {
        std::string css_content = readFile("styles.css");
        res.set_content(css_content, "text/css");
    });

    // معالجة إرسال النموذج
    svr.Post("/submit", [](const httplib::Request& req, httplib::Response& res) {
        auto name = req.get_param_value("name");
        auto email = req.get_param_value("email");
        auto service = req.get_param_value("service");

        // طباعة البيانات في الطرفية
        std::cout << "New service request:\nName: " << name << "\nEmail: " << email << "\nService: " << service << std::endl;

        // تكوين رسالة تأكيد
        std::string response_text = "Thank you " + name + " for requesting " + service + ". We will contact you via email: " + email + ".";
        res.set_content(response_text, "text/plain");
    });

    std::cout << "Server is running on http://localhost:8080\n";
    svr.listen("localhost", 8080);

    return 0;
}



</script>
