====================
*   Introduction   *
====================

This is a simple introductory application demonstrating how view templates are associated with RDF resources.

From the main folder, click on the new folder icon on the right. Create a new folder and in the edit tab of the new folder import the Hello World application helloworld.car.

====================
*     Details      *
====================

hello.html is a simple HTML file. HTML files are served with no processing. One can see the contents of hello.html immediately by requesting it. An HTTP request for helloworld.html (to the full URL, e.g. http://localhost:8080/helloworld/helloworld.html) will result in Callimachus serving the file. hello.html contains:

<html>
<body>
<p>Hello, World from HTML!</p>
</body>
</html>

That's useful, but not so interesting. Now let's see how Callimachus processes requests for other resources.

The HelloClass is a Callimachus Class with an associated view template of helloworld.xhtml.

helloworld.ttl is an RDF file in Turtle syntax. See the following URL for information about the Turtle format:

http://www.w3.org/TeamSubmission/turtle/

helloworld.ttl tells Callimachus that the resource hello+resource is a HelloClass?. The helloworld.ttl file contains the following statements.

@prefix calli:<http://callimachusproject.org/rdf/2009/framework#>.
@prefix rdfs:<http://www.w3.org/2000/01/rdf-schema#>.

# Create a resource with a label
<hello+resource> a <HelloClass>; rdfs:label "hello resource".
helloworld.xhtml is nearly identical in content to helloworld.html. The difference is that helloworld.xhtml is serialized as XHTML, associated with a class and passes through the Callimachus evaluation process prior to being served - because it is being used as a view template to another resource.

An HTTP request for hello+resource (to the full URL, e.g. http://localhost:8080/helloworld/hello+resource) will result in Callimachus looking at its RDF to determine if that resource is associated with a class with a view template. Seeing that it is, Callimachus will serve the file using the template helloworld.xhtml and you should see "Hello, World!" in your Web client.

Try creating own class and view template and associate your own resources to your class. Remember that you can make your HTML look pretty simply by adding a CSS stylesheet reference to it.