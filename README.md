Wicket Stuff HTML Validator
===========================

This validator filter is based upon the work of the validator filter created
by the Tuckey developers. This validator only validates XHTML based on the
XHTML DTDs. This package is licensed under the Gnu Public License.

We have provided the HTML Validator with extra settings to ignore non-DTD, but
generally useful and accepted practises, such as the "autocomplete=false"
attribute for text fields. We also added the ability to ignore a couple of
Wicket encoding bugs where & characters were not converted to proper entities.

Usage
-----

You can use it by adding the HtmlValidationResponseFilter to the Wicket 
request cycle filters in the following fashion:

	public class MyApplication extends WebApplication {
	    // ...
    
	    @Override
	    protected void init() {
	        // only enable the markup filter in DEVELOPMENT mode
	        if(DEVELOPMENT.equals(getConfigurationType())) {
		        HtmlValidationResponseFilter htmlvalidator = new HtmlValidationResponseFilter();
		        htmlvalidator.setIgnoreAutocomplete(true);
				htmlvalidator.setIgnoreKnownWicketBugs(true);
	            getRequestCycleSettings()
	                .addResponseFilter(htmlvalidator);
	        }
	    }
	}

And you're all set. Make sure you define a XHTML doctype in your pages, such
as:

	<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN"
	    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
	<html xmlns="http://www.w3.org/1999/xhtml">
	<head>
	    <title>Foo</title>
	</head>
	<body>
	</body>
	</html>

Include the following in your project's pom:

	<dependency>
	    <groupId>org.wicketstuff</groupId>
	    <artifactId>htmlvalidator</artifactId>
	    <version>1.5-rc3</version>
	    <scope>test</scope>
	</dependency>

If you wish to deploy the markup filter, you should change the scope to
compile.

The release has been published to the wicketstuff.org maven repository, found
at:

    http://wicketstuff.org/maven/repository

The release artifacts can be found at this URL:

    http://wicketstuff.org/maven/repository/org/wicketstuff/htmlvalidator/1.5-rc3/

Examples
--------
For examples, start the embedded Jetty server found in src/test/java

and go to http://localhost:8080

Building
--------

This project requires Apache Maven (>= 2.0.9) to be built. Check out the source code from the github repository and perform a

    mvn install

in the root folder of your checkout. Update your project's POM using the
SNAPSHOT GAV coordinates of the validator and follow the usage instructions.

Support
-------

Either ask a question on the [Wicket user mailing list](http://wicket.apache.org/help/email.html), or create a ticket at [Github/dashorst/wicket-stuff-markup-validator](https://github.com/dashorst/wicket-stuff-markup-validator/issues).

