# yellowSS
A CSS and Javascript framework for web page rendering based on Nodejs, socket.io and express.

### Installation :

    npm install yellowss

### Set up :

    var yellow = require('yellowss');
    yellow.load([ // Loading the yellow modules
        'essentials'
    ]);
    
    var globalAttributes = { // Website specifications
        sitename: 'YellowSS',
        encoding: 'utf-8',
        license: 'MIT',
        style: yellow(), // Loading the yellow script
        message: 'hello world'
    };
    
    yellow.synaptic.set('twig', globalAttributes, function() { //template engine | website specifications | callback
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
