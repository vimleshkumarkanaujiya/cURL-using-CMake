# cURL using CMake
A sample CMakeLists.txt file for building source with the cURL library
## Refer these steps to build the source <a href="https://github.com/vimleshkumarkanaujiya/CMake">CMake</a>

Code :

``` cpp
#include <crow.h>

int main()
{
    crow::SimpleApp app;

    CROW_ROUTE(app, "/")
    ([]() {
        // Get the index.html file
        std::ifstream file("index.html");
        if (file) {
            std::stringstream buffer;
            buffer << file.rdbuf();
            return buffer.str();
        } else {
            return "Error: Failed to load index.html";
        }
    });

    CROW_ROUTE(app, "/static/<string>")
    ([](const std::string& filename) {
        // Get static files (CSS, JavaScript, etc.)
        std::ifstream file("static/" + filename);
        if (file) {
            std::stringstream buffer;
            buffer << file.rdbuf();
            crow::response res(buffer.str());
            res.set_header("Content-Type", "text/" + crow::mustache::extension(filename));
            return res;
        } else {
            return crow::response(404, "File not found");
        }
    });

    app.port(8080).multithreaded().run();
}
```
