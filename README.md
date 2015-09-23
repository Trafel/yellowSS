# yellowSS
A CSS and Javascript framework for web page rendering based on Nodejs, socket.io and express.

### Installation :

    npm install yellowss

### Set up :

    var yellow = require('yellowss');
    yellow.load([ // Loading the yellow modules
        'essentials'
    ]);
    
    // Website specifications
    var globalAttributes = { 
        sitename: 'YellowSS',
        encoding: 'utf-8',
        license: 'MIT',
        style: yellow(), // Loading the yellow script
        message: 'hello world'
    };
    
    //template engine | website specifications | callback
    // In this case, twig is used for templating
    yellow.synaptic.set('twig', globalAttributes, function() { 
        io.on('connection', function(socket){ 
            console.log('A user visited your page !');
    });
    
    yellow.synaptic.control('/', 'index', {
        pagename: 'Index',
        link: '/',
        content: 'Index Content',
        script: 'console.log("hello world")',
        message: 'hey buddy !' // wich will erase the message set in website specifications
    });
    yellow.synaptic.control(404, '<h1>404: Page not found.</h1>');
    
    yellow.synaptic.initialize(8800, function() { // Listening
        console.log('Connexion initialized on port 8800');
    });

### Exemple of a twig template

(located on 'views' folder)

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>{{pagename}} | {{sitename}}</title>
        {{header}}
        {{style}}
    </head>
    <body id="{{pagename}}">
        <table id="wrapper">
            <tr id="header">
                <td>
                    <h1>Welcome</h1>
                </td>
            </tr>
            <tr id="content">
                <td>
                    <span class="set-background-color-blue absolute width-600 calibri">TEST</span>
                    <p><b>Page :</b> {{pagename}}</p>
                    <p><b>Site :</b> {{sitename}}</p>
                    <p><b>Url requested :</b> {{request.headers.host}}{{request.url}}</p>
                    <p><b>Navigation : <a href="{{link}}">to the next page ! ({{link}})</a></p>
                    <p><b>allocated content :</b> {{content}}</p>
                </td>
            </tr>
            <tr id="footer">
                <td>
                    <p>Footer</p>
                </td>
            </tr>
        </table>
    {{script}}
    </body>
    </html>
