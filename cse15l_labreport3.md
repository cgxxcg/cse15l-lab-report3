### Lab3 report
# Part1
## Code:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String message = "";
    int num = 0;

    public String handleRequest(URI url) {
        if( (url.getPath().equals("/"))){
            return "";
        }
        if (url.getPath().contains("/add-message")) { 
            String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")){
                String newMessage = parameters[1]; 
                num++;
                if (message.equals("") ){
                    message = num + ". " + newMessage;
                }
                else{
                    message = message + "\n" + num + ". " + newMessage;
                }
                return message;
                }
        }
        return "404 Not Found!";        
    }
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```
## Examples of using /add-message
<img width="794" alt="image" src="https://github.com/cgxxcg/cse15l-lab-report3/assets/146875584/c75272d3-edbd-4dac-a439-c9adbe4a94ed">


For this screenshot, after the main method is called, the handleRequest(URI url) method is called. The relevant argument is the URL of the webpage I launched running the StringServer.java file in the terminal given a port number on Edstem. This URL contains a "/add-message" query or it will return an empty string. In the class Handler, I created two fields which are an empty string named message and an integer named num with value 0. By first launching the port, the field doesn't change because there is no query in the URL. According to my code, when the URL path is "/", it returns an "" leaving a blank page. After adding messages five times (the last one is /add-message?s=ok), the field integer keeps track of how many messages are added by /add-message. The field message keeps updating with a format that contains the integer field, the newly added message, and all messages added previously. This is because I add the retains the original message and overrides it after execution of the new query.



<img width="814" alt="image" src="https://github.com/cgxxcg/cse15l-lab-report3/assets/146875584/b3747176-a42b-47fd-a662-9f193e7a73c1">

For this screenshot, after the main method is called, the handleRequest(URI url) method is called. The relevant argument is the URL of the webpage I launched running the StringServer.java file in the terminal given a port number on Edstem. This URL contains a "/add-message" query or it will return an empty string. In the class Handler, I created two fields which are an empty string named message and an integer named num with value 0. By first launching the port, the field doesn't change because there is no query in the URL. According to my code, when the URL path is "/", it returns an "" leaving a blank page. After adding messages four times, the field integer keeps track of how many messages are added by /add-message. The field message keeps updating with a format that contains the integer field, the newly added message, and all messages added previously. This is because I add the retains the original message and overrides it after execution of new query.


# Part2
<img width="458" alt="image" src="https://github.com/cgxxcg/cse15l-lab-report3/assets/146875584/bb52828f-d829-4693-b969-84d68ac62e3a">








terminal interaction (login to ieng6 without password):
<img width="1027" alt="image" src="https://github.com/cgxxcg/cse15l-lab-report3/assets/146875584/9597743e-d855-4e5c-8a1e-e3f7f7d61ad5">



# Part3
From lab2, I learned that curl command can be used to access URLs and print out what it accesses to the terminal. And by ssh, I can connect to another computer remotely and use different commands. 
