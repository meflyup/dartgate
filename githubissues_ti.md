# github问题

# gitbook-plugin-ace

<!--sec data-title="Introduction" data-id="intro" ces-->
This page is implemented using the two plugins developed by me: ```gitbook-plugin-ace```. Please check the [Github repo](https://github.com/ymcatar/gitbook-plugin-ace) for the syntax and changelog of the plugin.
<!--endsec-->

<!--sec data-title="Examples" data-id="example" ces-->

Here is the "Hello World" program of C language. The code editor in this section is set to be editable.

{%ace edit=true, lang='c_cpp'%}
#include <stdio.h>

int main(){
	int i;

	for(i=0; i<10; i++)
		printf("Hello World.");

	return 0;
}
{%endace%}

And a javascript code right here:

{%ace edit=false, lang='javascript'%}
var message = 'H e l l o W o r l d';
var split = message.split(' ').join('');
console.log(message);
{%endace%}

<!--endsec-->

And a piece of javascript code with wrong syntax, but with syntax validation disabled.

{%ace edit=false, lang='javascript', check=false%}
var test = [
	somethingIsWrong: 'withThis';
];
{%endace%}


#mermaid test
{% mermaid %}
graph TD;
  A-->B;
  A-->C;
  B-->D;
  C-->D;
{% endmermaid %}