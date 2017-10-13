## Q and A Content

#### Should JSON and XML formats, that lack so many H-Factors, be discouraged for implementing hypermedia?
The short answer is 'yes.' To implement hypermedia clients, you'll need information about the Objects, Addresses, and Actions that are allowed for a particular user at runtime. There are ways to use _addtional_ files to load with the XML/JSON data that hold the hypermedia information (see HAL-FORMS and POD) but these means the client has to understand more than one format in order to interact with yuor serv ices.

### What happens when the data is served by a backend service like a database?
Serving data directly from the DB to the web is pretty tricky. Any change in the data tables means a change in the representation and databases don't usually output any OAA information the client can use. Typically, the best thing to do is to place a translator between the API and the storage. Usually that's some code that converts the raw data into objects and then the objects into a web format (like XML/JSON or a hypewrmedia format). Check out the Message Translator pattern from Gregor Hohpe and the WeSTL format for ideas on how to do this.

### Isn't it better and efficient to make Id out of the template and use this template to send to the client. The client itself then uses the id to lookup the actual template cache it and consume it?
'Better' might be debatable but that's certainly an option. This is essentially the POV of HAL designer, Mike Kelly. He doesn't think responses should include FORMS. Instead he likes to put that into code. Others have used an external format (like HAL-FORMS) to do the same thing. w/ HAL-FORMS, the actions are separate representations with their own unique resource ids (URLs) and clients cna chose to cache them separately to save space/time.
