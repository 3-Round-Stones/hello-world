====================
*   Introduction   *
====================

This is a simple introductory application demonstrating how view templates are associated with RDF resources.

  1. Access the Home Folder my clicking the main menu in the upper right and selecting "Home folder"
  2. From there, select the red "Create" dropdown and choose "Folder".
  3. Name your folder and click "Create".
  4. Click the main menu and select "Import folder contents"
  5. Click "Choose files" and select the Hello World Callimachus ARchive (CAR) - helloworld.car.

====================
*     Details      *
====================

helloworld.html is a simple HTML file. HTML files are served with no pre-processing on the part of Callimachus. This means that no additional HTML, CSS, or JavaScript is added. One can see the contents of helloworld.html immediately by clicking on it from the folder view. An HTTP request for helloworld.html (to the full URL, e.g. http://localhost:8080/helloworld/helloworld.html) will result in Callimachus serving the file verbatim. helloworld.html contains:

[[
<html>
	<body>
		<p>Hello, World from HTML!</p>
	</body>
</html>
]]

That's useful, but not so interesting. Now let's see how Callimachus processes requests for other resources. The HelloClass is a Callimachus Class with an associated view template of helloworld.xhtml. Note the extension here is Xhtml, not plain html.

helloworld.ttl is an RDF file in Turtle syntax. See the following URL for information about the Turtle format:

http://www.w3.org/TeamSubmission/turtle/

helloworld.ttl tells Callimachus that the resource hello+resource is an instance of HelloClass. The helloworld.ttl file contains the following statements.

[[
@prefix calli:<http://callimachusproject.org/rdf/2009/framework#>.
@prefix rdfs:<http://www.w3.org/2000/01/rdf-schema#>.

# Create a resource with a label
<hello+resource> a <HelloClass>
	; rdfs:label "hello resource"
.
]]

helloworld.xhtml is nearly identical in content to helloworld.html. The difference is that helloworld.xhtml is serialized as XHTML, associated with a class and passes through the Callimachus evaluation process prior to being served - because it is being used as a view template to another resource (in this case, the HelloWorld class).

An HTTP request for hello+resource (to the full URL, e.g. http://localhost:8080/helloworld/hello+resource) will result in Callimachus looking at its RDF to determine if that resource is associated with a class that uses a view template. Seeing that it is, Callimachus will serve the file using the template helloworld.xhtml and you should see "Hello, World!" in your Web client.

Try creating own class and view template and associate your own resources to your class. Remember that you can make your HTML look pretty simply by adding a CSS stylesheet reference to it.