# Mindmap-
Darshana
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mindmap Manager - Cross Platform</title>
    <meta name="description" content="Upload, organize, and access your Mindomo mindmaps across all devices">
    <meta name="author" content="Mindmap Manager">
    
    <!-- PWA Meta Tags -->
    <meta name="theme-color" content="#667eea">
    <meta name="apple-mobile-web-app-capable" content="yes">
    <meta name="apple-mobile-web-app-status-bar-style" content="default">
    <meta name="apple-mobile-web-app-title" content="Mindmap Manager">
    
    <!-- Favicon -->
    <link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🧠</text></svg>">
    
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            color: #333;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 20px;
        }

        .header {
            text-align: center;
            margin-bottom: 40px;
            color: white;
        }

        .header h1 {
            font-size: 2.5rem;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.3);
        }

        .header p {
            font-size: 1.1rem;
            opacity: 0.9;
        }

        .main-content {
            background: rgba(255, 255, 255, 0.95);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 20px 40px rgba(0,0,0,0.1);
            backdrop-filter: blur(10px);
        }

        .upload-section {
            text-align: center;
            margin-bottom: 40px;
            padding: 40px;
            border: 2px dashed #667eea;
            border-radius: 15px;
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
            transition: all 0.3s ease;
        }

        .upload-section:hover {
            border-color: #764ba2;
            transform: translateY(-2px);
            box-shadow: 0 10px 20px rgba(102, 126, 234, 0.2);
        }

        .upload-icon {
            font-size: 4rem;
            color: #667eea;
            margin-bottom: 20px;
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0px); }
            50% { transform: translateY(-10px); }
        }

        .upload-input {
            display: none;
        }

        .upload-btn {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 15px 30px;
            border: none;
            border-radius: 50px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: all 0.3s ease;
            box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
        }

        .upload-btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 8px 25px rgba(102, 126, 234, 0.4);
        }

        .file-list {
            margin-top: 30px;
        }

        .file-item {
            background: white;
            border: 1px solid #e0e0e0;
            border-radius: 10px;
            padding: 20px;
            margin-bottom: 15px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            transition: all 0.3s ease;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }

        .file-item:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 20px rgba(0,0,0,0.1);
        }

        .file-info {
            display: flex;
            align-items: center;
            flex-grow: 1;
        }

        .file-icon {
            font-size: 2rem;
            color: #667eea;
            margin-right: 15px;
        }

        .file-details h3 {
            color: #333;
            margin-bottom: 5px;
        }

        .file-details p {
            color: #666;
            font-size: 0.9rem;
        }

        .file-actions {
            display: flex;
            gap: 10px;
        }

        .action-btn {
            padding: 8px 16px;
            border: none;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
            transition: all 0.3s ease;
        }

        .view-btn {
            background: #4CAF50;
            color: white;
        }

        .download-btn {
            background: #2196F3;
            color: white;
        }

        .delete-btn {
            background: #f44336;
            color: white;
        }

        .action-btn:hover {
            transform: scale(1.05);
        }

        .stats {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 20px;
            margin-bottom: 40px;
        }

        .stat-card {
            background: linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%);
            padding: 20px;
            border-radius: 15px;
            text-align: center;
            border: 1px solid rgba(102, 126, 234, 0.2);
        }

        .stat-number {
            font-size: 2rem;
            font-weight: bold;
            color: #667eea;
            margin-bottom: 5px;
        }

        .stat-label {
            color: #666;
            font-size: 0.9rem;
        }

        .search-bar {
            width: 100%;
            padding: 15px 20px;
            border: 1px solid #e0e0e0;
            border-radius: 50px;
            font-size: 1rem;
            margin-bottom: 30px;
            outline: none;
            transition: all 0.3s ease;
        }

        .search-bar:focus {
            border-color: #667eea;
            box-shadow: 0 0 20px rgba(102, 126, 234, 0.2);
        }

        .empty-state {
            text-align: center;
            padding: 60px 20px;
            color: #666;
        }

        .empty-state-icon {
            font-size: 4rem;
            margin-bottom: 20px;
            opacity: 0.5;
        }

        /* Modal Styles */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            background: rgba(0, 0, 0, 0.8);
            z-index: 10000;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }

        .modal-content {
            background: white;
            border-radius: 15px;
            max-width: 90vw;
            max-height: 90vh;
            overflow: hidden;
            box-shadow: 0 20px 40px rgba(0, 0, 0, 0.3);
            display: flex;
            flex-direction: column;
        }

        .modal-header {
            padding: 20px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .modal-header h2 {
            margin: 0;
            font-size: 1.3rem;
        }

        .close-btn {
            background: rgba(255, 255, 255, 0.2);
            border: none;
            color: white;
            font-size: 1.5rem;
            width: 40px;
            height: 40px;
            border-radius: 50%;
            cursor: pointer;
            display: flex;
            align-items: center;
            justify-content: center;
            transition: background 0.3s ease;
        }

        .close-btn:hover {
            background: rgba(255, 255, 255, 0.3);
        }

        .viewer-content {
            padding: 20px;
            overflow: auto;
            flex: 1;
        }

        .metadata-info {
            background: #e3f2fd;
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 20px;
            color: #1565c0;
            font-family: monospace;
        }

        .mindmap-tree {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            line-height: 1.6;
        }

        .mindmap-node {
            margin: 8px 0;
            padding-left: 20px;
            border-left: 2px solid #ddd;
            position: relative;
        }

        .mindmap-node::before {
            content: '';
            position: absolute;
            left: -2px;
            top: 15px;
            width: 8px;
            height: 2px;
            background: #ddd;
        }

        .mindmap-node-text {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 10px 16px;
            border-radius: 25px;
            display: inline-block;
            margin-bottom: 10px;
            box-shadow: 0 3px 10px rgba(102, 126, 234, 0.3);
            font-weight: 500;
            max-width: calc(100% - 40px);
            word-wrap: break-word;
            position: relative;
        }

        .mindmap-node-text.level-0 {
            font-size: 1.3em;
            font-weight: bold;
            background: linear-gradient(135deg, #764ba2 0%, #667eea 100%);
            box-shadow: 0 4px 15px rgba(118, 75, 162, 0.4);
        }

        .mindmap-node-text.level-1 {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            font-size: 1.1em;
        }

        .mindmap-node-text.level-2 {
            background: linear-gradient(135deg, #ff9800 0%, #f57c00 100%);
            font-size: 1em;
        }

        .mindmap-node-text.level-3 {
            background: linear-gradient(135deg, #e91e63 0%, #c2185b 100%);
            font-size: 0.95em;
        }

        .mindmap-node-text.level-4 {
            background: linear-gradient(135deg, #9c27b0 0%, #7b1fa2 100%);
            font-size: 0.9em;
        }

        .mindmap-children {
            margin-left: 15px;
            margin-top: 10px;
        }

        .node-tag-info {
            font-size: 0.7em;
            opacity: 0.8;
            background: rgba(255,255,255,0.2);
            padding: 2px 6px;
            border-radius: 10px;
            margin-left: 8px;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                padding: 10px;
            }

            .main-content {
                padding: 20px;
            }

            .header h1 {
                font-size: 2rem;
            }

            .file-item {
                flex-direction: column;
                align-items: flex-start;
                gap: 15px;
            }

            .file-actions {
                align-self: stretch;
                justify-content: center;
            }

            .stats {
                grid-template-columns: repeat(2, 1fr);
            }
        }

        @media (max-width: 480px) {
            .stats {
                grid-template-columns: 1fr;
            }

            .upload-section {
                padding: 20px;
            }

            .upload-icon {
                font-size: 3rem;
            }
        }

        .platform-indicator {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: rgba(0,0,0,0.8);
            color: white;
            padding: 10px 15px;
            border-radius: 20px;
            font-size: 0.8rem;
            z-index: 1000;
        }

        .footer {
            text-align: center;
            margin-top: 40px;
            padding: 20px;
            color: rgba(255, 255, 255, 0.7);
            font-size: 0.9rem;
        }

        .install-prompt {
            background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
            color: white;
            padding: 15px;
            border-radius: 10px;
            margin-bottom: 20px;
            display: none;
            align-items: center;
            justify-content: space-between;
        }

        .install-btn {
            background: rgba(255, 255, 255, 0.2);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 20px;
            cursor: pointer;
            font-size: 0.9rem;
        }
    </style>
</head>
<body>
    <div class="platform-indicator" id="platformIndicator">
        📱 Platform: <span id="platformName">Loading...</span>
    </div>

    <div class="container">
        <div class="header">
            <h1>🧠 Mindmap Manager</h1>
            <p>Upload, organize, and access your Mindomo mindmaps across all devices</p>
        </div>

        <div class="main-content">
            <div class="install-prompt" id="installPrompt">
                <div>
                    📱 Install this app on your device for offline access!
                </div>
                <button class="install-btn" id="installBtn">Install</button>
            </div>

            <div class="stats">
                <div class="stat-card">
                    <div class="stat-number" id="totalFiles">0</div>
                    <div class="stat-label">Total Mindmaps</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="totalSize">0 MB</div>
                    <div class="stat-label">Storage Used</div>
                </div>
                <div class="stat-card">
                    <div class="stat-number" id="lastUpload">Never</div>
                    <div class="stat-label">Last Upload</div>
                </div>
            </div>

            <div class="upload-section" onclick="document.getElementById('fileInput').click()">
                <div class="upload-icon">📁</div>
                <h2>Upload Your Mindmaps</h2>
                <p style="margin: 15px 0;">Drag and drop files here or click to browse</p>
                <p style="font-size: 0.9rem; color: #666;">Supports: .mmap, .xml, .mm, .json, .pdf, .png, .jpg</p>
                <input type="file" id="fileInput" class="upload-input" multiple accept=".mmap,.xml,.mm,.json,.pdf,.png,.jpg,.jpeg">
                <button class="upload-btn">Choose Files</button>
            </div>

            <input type="text" class="search-bar" id="searchBar" placeholder="🔍 Search your mindmaps...">

            <div class="file-list" id="fileList">
                <div class="empty-state">
                    <div class="empty-state-icon">🗂️</div>
                    <h3>No mindmaps uploaded yet</h3>
                    <p>Upload your first mindmap to get started</p>
                </div>
            </div>
        </div>

        <div class="footer">
            <p>🌐 Hosted on GitHub Pages • Works offline • Privacy-focused</p>
            <p>Made with ❤️ for mindmap enthusiasts</p>
        </div>
    </div>

    <script>
        // Platform detection and display
        function detectPlatform() {
            const userAgent = navigator.userAgent.toLowerCase();
            const platform = navigator.platform.toLowerCase();
            
            let platformName = 'Unknown';
            let emoji = '💻';
            
            if (/ipad/.test(userAgent) || (platform === 'macintel' && navigator.maxTouchPoints > 1)) {
                platformName = 'iPad';
                emoji = '📱';
            } else if (/iphone/.test(userAgent)) {
                platformName = 'iPhone';
                emoji = '📱';
            } else if (/android/.test(userAgent)) {
                platformName = 'Android';
                emoji = '🤖';
            } else if (/mac/.test(platform)) {
                platformName = 'MacBook/Mac';
                emoji = '💻';
            } else if (/win/.test(platform)) {
                platformName = 'Windows';
                emoji = '🖥️';
            } else if (/linux/.test(userAgent)) {
                platformName = 'Linux';
                emoji = '🐧';
            }
            
            document.getElementById('platformName').textContent = platformName;
            document.getElementById('platformIndicator').innerHTML = `${emoji} Platform: <span>${platformName}</span>`;
        }

        // PWA Installation
        let deferredPrompt;
        
        window.addEventListener('beforeinstallprompt', (e) => {
            e.preventDefault();
            deferredPrompt = e;
            document.getElementById('installPrompt').style.display = 'flex';
        });

        document.getElementById('installBtn').addEventListener('click', async () => {
            if (deferredPrompt) {
                deferredPrompt.prompt();
                const { outcome } = await deferredPrompt.userChoice;
                if (outcome === 'accepted') {
                    document.getElementById('installPrompt').style.display = 'none';
                }
                deferredPrompt = null;
            }
        });

        // File management
        let uploadedFiles = [];
        let fileIdCounter = 1;

        function formatFileSize(bytes) {
            if (bytes === 0) return '0 Bytes';
            const k = 1024;
            const sizes = ['Bytes', 'KB', 'MB', 'GB'];
            const i = Math.floor(Math.log(bytes) / Math.log(k));
            return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
        }

        function getFileIcon(filename) {
            const ext = filename.toLowerCase().split('.').pop();
            const iconMap = {
                'mmap': '🧠',
                'xml': '📄',
                'mm': '🗺️',
                'json': '📋',
                'pdf': '📕',
                'png': '🖼️',
                'jpg': '🖼️',
                'jpeg': '🖼️'
            };
            return iconMap[ext] || '📄';
        }

        function addFile(file) {
            const fileObj = {
                id: fileIdCounter++,
                name: file.name,
                size: file.size,
                type: file.type,
                uploadDate: new Date(),
                file: file
            };
            
            uploadedFiles.push(fileObj);
            updateStats();
            renderFileList();
        }

        function deleteFile(fileId) {
            uploadedFiles = uploadedFiles.filter(f => f.id !== fileId);
            updateStats();
            renderFileList();
        }

        function downloadFile(fileId) {
            const file = uploadedFiles.find(f => f.id === fileId);
            if (file) {
                const url = URL.createObjectURL(file.file);
                const a = document.createElement('a');
                a.href = url;
                a.download = file.name;
                document.body.appendChild(a);
                a.click();
                document.body.removeChild(a);
                URL.revokeObjectURL(url);
            }
        }

        function viewFile(fileId) {
            const file = uploadedFiles.find(f => f.id === fileId);
            if (file) {
                const ext = file.name.toLowerCase().split('.').pop();
                
                if (['xml', 'mm', 'mmap', 'json'].includes(ext)) {
                    showMindmapViewer(file);
                } else {
                    const url = URL.createObjectURL(file.file);
                    window.open(url, '_blank');
                }
            }
        }

        function showMindmapViewer(file) {
            const reader = new FileReader();
            reader.onload = function(e) {
                const content = e.target.result;
                const ext = file.name.toLowerCase().split('.').pop();
                
                let parsedData;
                try {
                    if (ext === 'json') {
                        parsedData = JSON.parse(content);
                        displayJSONMindmap(file.name, parsedData);
                    } else if (ext === 'xml' || ext === 'mm' || ext === 'mmap') {
                        parsedData = parseXMLMindmap(content);
                        displayXMLMindmap(file.name, parsedData);
                    }
                } catch (error) {
                    displayRawContent(file.name, content, `Error parsing ${ext.toUpperCase()} file: ${error.message}`);
                }
            };
            reader.readAsText(file.file);
        }

        function parseXMLMindmap(xmlContent) {
            const parser = new DOMParser();
            const xmlDoc = parser.parseFromString(xmlContent, 'text/xml');
            
            // Check for XML parsing errors
            const parserError = xmlDoc.querySelector('parsererror');
            if (parserError) {
                throw new Error('XML parsing failed: ' + parserError.textContent);
            }
            
            // Try multiple approaches to find the root node
            let rootNode = null;
            
            // Approach 1: Standard FreeMind format
            rootNode = xmlDoc.querySelector('map node');
            
            // Approach 2: Direct node element
            if (!rootNode) {
                rootNode = xmlDoc.querySelector('node');
            }
            
            // Approach 3: Root element approaches
            if (!rootNode) {
                const possibleRoots = ['root', 'mindmap', 'map', 'diagram', 'tree'];
                for (const rootName of possibleRoots) {
                    rootNode = xmlDoc.querySelector(rootName);
                    if (rootNode) break;
                }
            }
            
            // Approach 4: Any element with TEXT or title attribute
            if (!rootNode) {
                const elementsWithText = xmlDoc.querySelectorAll('*[TEXT], *[text], *[title], *[name]');
                if (elementsWithText.length > 0) {
                    rootNode = elementsWithText[0];
                }
            }
            
            // Approach 5: Use document root element if nothing else works
            if (!rootNode) {
                rootNode = xmlDoc.documentElement;
            }
            
            // If still no root found, show the raw content
            if (!rootNode) {
                throw new Error('Could not identify mindmap structure. The file may be in an unsupported format.');
            }
            
            function parseNode(node, level = 0) {
                // Try multiple ways to get the node text
                let text = node.getAttribute('TEXT') || 
                          node.getAttribute('text') || 
                          node.getAttribute('title') || 
                          node.getAttribute('name') || 
                          node.getAttribute('label') ||
                          node.textContent?.trim() ||
                          node.tagName;
                
                // Clean up the text
                if (text && text.length > 100) {
                    text = text.substring(0, 100) + '...';
                }
                
                const children = [];
                
                // Try multiple ways to find child nodes
                let childNodes = [];
                
                // Method 1: Direct child nodes
                const directNodes = Array.from(node.children).filter(child => 
                    child.tagName.toLowerCase() === 'node' || 
                    child.hasAttribute('TEXT') || 
                    child.hasAttribute('text') || 
                    child.hasAttribute('title')
                );
                
                // Method 2: Any child elements that might be nodes
                if (directNodes.length === 0) {
                    childNodes = Array.from(node.children).filter(child => 
                        child.nodeType === 1 && // Element node
                        child.tagName !== 'style' && 
                        child.tagName !== 'script'
                    );
                } else {
                    childNodes = directNodes;
                }
                
                childNodes.forEach(child => {
                    children.push(parseNode(child, level + 1));
                });
                
                return {
                    text: text || 'Untitled Node',
                    level: level,
                    children: children,
                    id: node.getAttribute('ID') || node.getAttribute('id') || Math.random().toString(36).substr(2, 9),
                    tagName: node.tagName
                };
            }
            
            const result = parseNode(rootNode);
            
            // Add some metadata about the parsed structure
            result.metadata = {
                totalNodes: xmlDoc.querySelectorAll('*').length,
                rootTagName: rootNode.tagName,
                hasStandardFormat: !!xmlDoc.querySelector('map node')
            };
            
            return result;
        }

        function displayXMLMindmap(filename, data) {
            const modal = createViewerModal(filename);
            const content = modal.querySelector('.viewer-content');
            
            const metadataInfo = data.metadata ? `
                <div class="metadata-info">
                    <small>📊 Parsed ${data.metadata.totalNodes} elements | Root: ${data.metadata.rootTagName} | Format: ${data.metadata.hasStandardFormat ? 'Standard' : 'Custom'}</small>
                </div>
            ` : '';
            
            content.innerHTML = `
                ${metadataInfo}
                <div class="mindmap-tree">
                    ${renderMindmapNode(data)}
                </div>
            `;
        }

        function renderMindmapNode(node) {
            const levelClass = `level-${Math.min(node.level, 4)}`;
            const tagInfo = node.tagName && node.tagName !== 'node' ? `<span class="node-tag-info">${node.tagName}</span>` : '';
            
            let html = `
                <div class="mindmap-node">
                    <div class="mindmap-node-text ${levelClass}">
                        ${escapeHtml(node.text)}
                        ${tagInfo}
                    </div>
            `;
            
            if (node.children && node.children.length > 0) {
                html += '<div class="mindmap-children">';
                node.children.forEach(child => {
                    html += renderMindmapNode(child);
                });
                html += '</div>';
            }
            
            html += '</div>';
            return html;
        }

        function displayJSONMindmap(filename, data) {
            const modal = createViewerModal(filename);
            const content = modal.querySelector('.viewer-content');
            
            content.innerHTML = `
                <div class="json-viewer">
                    <pre>${JSON.stringify(data, null, 2)}</pre>
                </div>
                <style>
                    .json-viewer pre {
                        background: #f8f9fa;
                        padding: 20px;
                        border-radius: 10px;
                        overflow: auto;
                        max-height: 600px;
                        font-family: 'Monaco', 'Consolas', monospace;
                        font-size: 14px;
                        line-height: 1.5;
                        color: #333;
                        border: 1px solid #e9ecef;
                    }
                </style>
            `;
        }

        function displayRawContent(filename, content, errorMessage = null) {
            const modal = createViewerModal(filename);
            const modalContent = modal.querySelector('.viewer-content');
            
            modalContent.innerHTML = `
                ${errorMessage ? `<div class="error-message">${errorMessage}</div>` : ''}
                <div class="raw-content">
                    <h4>Raw Content:</h4>
                    <pre>${escapeHtml(content)}</pre>
                </div>
                <style>
                    .error-message {
                        background: #f8d7da;
                        color: #721c24;
                        padding: 15px;
                        border-radius: 5px;
                        margin-bottom: 20px;
                        border: 1px solid #f5c6cb;
                    }
                    .raw-content pre {
                        background: #f8f9fa;
                        padding: 20px;
                        border-radius: 10px;
                        overflow: auto;
                        max-height: 500px;
                        font-family: 'Monaco', 'Consolas', monospace;
                        font-size: 12px;
                        line-height: 1.4;
                        color: #333;
                        border: 1px solid #e9ecef;
                        white-space: pre-wrap;
                        word-wrap: break-word;
                    }
                </style>
            `;
        }

        function createViewerModal(filename) {
            const modal = document.createElement('div');
            modal.className = 'modal-overlay';
            modal.innerHTML = `
                <div class="modal-content">
                    <div class="modal-header">
                        <h2>📄 ${escapeHtml(filename)}</h2>
                        <button class="close-btn" onclick="this.closest('.modal-overlay').remove()">✕</button>
                    </div>
                    <div class="viewer-content">
                        Loading...
                    </div>
                </div>
            `;
            
            document.body.appendChild(modal);
            
            // Close on background click
            modal.addEventListener('click', function(e) {
                if (e.target === modal) {
                    modal.remove();
                }
            });
            
            // Close on Escape key
            document.addEventListener('keydown', function(e) {
                if (e.key === 'Escape' && document.contains(modal)) {
                    modal.remove();
                }
            });
            
            return modal;
        }

        function escapeHtml(text) {
            const div = document.createElement('div');
            div.textContent = text;
            return div.innerHTML;
        }

        function updateStats() {
            document.getElementById('totalFiles').textContent = uploadedFiles.length;
            
            const totalSize = uploadedFiles.reduce((sum, file) => sum + file.size, 0);
            document.getElementById('totalSize').textContent = formatFileSize(totalSize);
            
            const lastUpload = uploadedFiles.length > 0 ? 
                uploadedFiles[uploadedFiles.length - 1].uploadDate.toLocaleDateString() : 'Never';
            document.getElementById('lastUpload').textContent = lastUpload;
        }

        function renderFileList(filteredFiles = uploadedFiles) {
            const fileList = document.getElementById('fileList');
            
            if (filteredFiles.length === 0) {
                fileList.innerHTML = `
                    <div class="empty-state">
                        <div class="empty-state-icon">🗂️</div>
                        <h3>${uploadedFiles.length === 0 ? 'No mindmaps uploaded yet' : 'No matching files found'}</h3>
                        <p>${uploadedFiles.length === 0 ? 'Upload your first mindmap to get started' : 'Try a different search term'}</p>
                    </div>
                `;
                return;
            }

            fileList.innerHTML = filteredFiles.map(file => `
                <div class="file-item">
                    <div class="file-info">
                        <div class="file-icon">${getFileIcon(file.name)}</div>
                        <div class="file-details">
                            <h3>${file.name}</h3>
                            <p>${formatFileSize(file.size)} • Uploaded ${file.uploadDate.toLocaleDateString()}</p>
                        </div>
                    </div>
                    <div class="file-actions">
                        <button class="action-btn view-btn" onclick="viewFile(${file.id})">👁️ View</button>
                        <button class="action-btn download-btn" onclick="downloadFile(${file.id})">⬇️ Download</button>
                        <button class="action-btn delete-btn" onclick="deleteFile(${file.id})">🗑️ Delete</button>
                    </div>
                </div>
            `).join('');
        }

        // Event listeners
        document.getElementById('fileInput').addEventListener('change', function(e) {
            Array.from(e.target.files).forEach(addFile);
        });

        document.getElementById('searchBar').addEventListener('input', function(e) {
            const searchTerm = e.target.value.toLowerCase();
            const filtered = uploadedFiles.filter(file => 
                file.name.toLowerCase().includes(searchTerm)
            );
            renderFileList(filtered);
        });

        // Drag and drop functionality
        const uploadSection = document.querySelector('.upload-section');

        uploadSection.addEventListener('dragover', function(e) {
            e.preventDefault();
            this.style.borderColor = '#764ba2';
            this.style.background = 'linear-gradient(135deg, rgba(118, 75, 162, 0.2) 0%, rgba(102, 126, 234, 0.2) 100%)';
        });

        uploadSection.addEventListener('dragleave', function(e) {
            e.preventDefault();
            this.style.borderColor = '#667eea';
            this.style.background = 'linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%)';
        });

        uploadSection.addEventListener('drop', function(e) {
            e.preventDefault();
            this.style.borderColor = '#667eea';
            this.style.background = 'linear-gradient(135deg, rgba(102, 126, 234, 0.1) 0%, rgba(118, 75, 162, 0.1) 100%)';
            
            Array.from(e.dataTransfer.files).forEach(addFile);
        });

        // Initialize
        detectPlatform();
        updateStats();
        renderFileList();

        // Service Worker for offline functionality
        if ('serviceWorker' in navigator) {
            window.addEventListener('load', function() {
                navigator.serviceWorker.register('sw.js').then(function(registration) {
                    console.log('SW registered: ', registration);
                }, function(registrationError) {
                    console.log('SW registration failed: ', registrationError);
                });
            });
        }
    </script>
</body>
</html>
