Hello future student!

This post will show what I did for my search engine and testing.



Part 1:


import java.io.IOException;
import java.net.URI;
import java.io.*; 
import java.util.*; 

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    int num = 0;

    ArrayList<String> strArray = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/add")) {
            //System.out.println("Path: " + url.getPath());
            //System.out.println("Adding");
            String[] parameters = url.getQuery().split("=");
            strArray.add(parameters[1]);
            /*for (int i = 0; i < parameters.length; i++) {
                //System.out.println(parameters[i]);
            }*/
            return "String " + parameters[1] + " added to list";
        }
        else if (url.getPath().equals("/search")) {
            //System.out.println("Path: " + url.getPath());
            String[] parameters = url.getQuery().split("=");
            String returnValues = "Strings in the list that contain " + parameters[1] + ":";
            for (int i = 0; i < strArray.size(); i++) {
                System.out.println("i equals: " + i);
                if (strArray.get(i).contains(parameters[1])) {
                    returnValues = returnValues.concat("\n" + strArray.get(i));
                    //System.out.println("Concatenating " + strArray.get(i));
                    //System.out.println("Return Values: " + returnValues);
                }
            }
            return returnValues;
        }
        else {
            return "404 Not Found!";
        }
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}

![Add #1](./search%20engine%201.png)
![Add #2](./search%20engine%202.png)
![Add #3](./search%20engine%203.png)
![Add #4](./search%20engine%204.png)
![Add #5](./search%20engine%205.png)

These 5 add queries use this add code:
![Add Code](./search%20engine%20add.png)

The return values are all modified by the parameters (specifically parameters[1], the first argument after the path) created by splitting up the URL after the path. This value is added to the strArray, and then is displayed in the return value.


And the searches:
![Search #1](./search%20engine%206.png)
![Search #2](./search%20engine%207.png)

Use this search code:
![Search Code](./search%20engine%20search.png)
Just like with adding, the search term is found by using split, and is at index 1 in parameters. The contains string method is used to get all of the strArray contents that contain the search parameter. The returnValue has all of these concatenated to it (along with a newline).







Part 2:















