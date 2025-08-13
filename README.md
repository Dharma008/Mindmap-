<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>ग्रन्थाः Mindmap Viewer</title>
    <!-- For online: Use CDNs -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/jstree/3.3.16/themes/default/style.min.css" />
    <script src="https://cdnjs.cloudflare.com/ajax/libs/jstree/3.3.16/jstree.min.js"></script>
    
    <!-- For offline: Comment out CDNs above and uncomment these (assuming files are downloaded locally) -->
    <!-- <script src="jquery.min.js"></script> -->
    <!-- <link rel="stylesheet" href="style.min.css" /> -->
    <!-- <script src="jstree.min.js"></script> -->
    
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; }
        #container { display: flex; height: 100vh; }
        #tree { width: 30%; overflow-y: auto; padding: 10px; border-right: 1px solid #ccc; }
        #content { width: 70%; height: 100%; border: none; }
    </style>
</head>
<body>
    <div id="container">
        <div id="tree"></div>
        <iframe id="content"></iframe>
    </div>
    
    <script>
        var treeData = [
            {
                "text": "ग्रन्थाः",
                "state": { "opened": true },
                "children": [
                    {
                        "text": "उपनिषदाः",
                        "children": [
                            { "text": "सर्वा उपनिषदः", "data": { "file": "सर्वा उपनिषदः.html" } },
                            { "text": "_सर्वा उपनिषदः मूलम्", "data": { "file": "_सर्वा उपनिषदः मूलम्.html" } }
                        ]
                    },
                    {
                        "text": "तर्क सग्रहः",
                        "children": [
                            { "text": "तर्क सग्रहः", "data": { "file": "तर्क सग्रहः.html" } },
                            { "text": "तर्क सग्रहः न्यायवोधिनी", "data": { "file": "तर्क सग्रहः न्यायवोधिनी.html" } }
                        ]
                    },
                    {
                        "text": "व्याकरणम्",
                        "children": [
                            { "text": "अष्टाध्यायी (1)", "data": { "file": "अष्टाध्यायी (1).html" } },
                            { "text": "समास", "data": { "file": "समास.html" } }
                        ]
                    },
                    { "text": "योग दर्शन  अथ पातञ्जलयोगदर्शनम", "data": { "file": "योग दर्शन  अथ पातञ्जलयोगदर्शनम.html" } },
                    { "text": "कथासरित सागर (3)", "data": { "file": "कथासरित सागर (3).html" } },
                    { "text": "अर्थ संग्रहः", "data": { "file": "अर्थ संग्रहः.html" } }
                ]
            }
        ];

        $('#tree').jstree({
            'core': {
                'data': treeData,
                'themes': { 'variant': 'large' }  // For better readability
            }
        }).on('select_node.jstree', function (e, data) {
            var node = data.node;
            if (node.data && node.data.file) {
                $('#content').attr('src', node.data.file);
            } else {
                $('#content').attr('src', '');  // Clear iframe if non-leaf node selected
            }
        });
    </script>
</body>
</html>
