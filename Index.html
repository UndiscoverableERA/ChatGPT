/** @jsxImportSource https://esm.sh/react@18.2.0 */
import React, { useState } from "https://esm.sh/react@18.2.0";
import { createRoot } from "https://esm.sh/react-dom@18.2.0/client";

function App() {
  const [image, setImage] = useState<string | null>(null);
  const [analysis, setAnalysis] = useState<string | null>(null);
  const [isLoading, setIsLoading] = useState(false);

  const handleImageUpload = async (e: React.ChangeEvent<HTMLInputElement>) => {
    const file = e.target.files?.[0];
    if (file) {
      const reader = new FileReader();
      reader.onloadend = () => {
        setImage(reader.result as string);
      };
      reader.readAsDataURL(file);
    }
  };

  const analyzeImage = async () => {
    if (!image) return;
    
    setIsLoading(true);
    try {
      const response = await fetch('/analyze', {
        method: 'POST',
        body: JSON.stringify({ image })
      });
      const result = await response.text();
      setAnalysis(result);
    } catch (error) {
      setAnalysis('Error analyzing image');
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <div style={styles.container}>
      <h1>🔍 Image Analyzer</h1>
      <input 
        type="file" 
        accept="image/*" 
        onChange={handleImageUpload}
        style={styles.fileInput}
      />
      {image && (
        <div style={styles.imageContainer}>
          <img 
            src={image} 
            alt="Uploaded" 
            style={styles.uploadedImage} 
          />
          <button 
            onClick={analyzeImage} 
            disabled={isLoading}
            style={styles.analyzeButton}
          >
            {isLoading ? '🔄 Analyzing...' : '🧐 Analyze Image'}
          </button>
        </div>
      )}
      {analysis && (
        <div style={styles.analysisContainer}>
          <h2>Analysis Result:</h2>
          <p>{analysis}</p>
        </div>
      )}
      <a 
        href={import.meta.url.replace("esm.town", "val.town")} 
        target="_top" 
        style={styles.sourceLink}
      >
        View Source
      </a>
    </div>
  );
}

const styles = {
  container: {
    fontFamily: 'Arial, sans-serif',
    maxWidth: '600px',
    margin: '0 auto',
    padding: '20px',
    textAlign: 'center',
  },
  fileInput: {
    margin: '20px 0',
  },
  imageContainer: {
    display: 'flex',
    flexDirection: 'column',
    alignItems: 'center',
  },
  uploadedImage: {
    maxWidth: '100%',
    maxHeight: '400px',
    objectFit: 'contain',
    marginBottom: '20px',
  },
  analyzeButton: {
    padding: '10px 20px',
    backgroundColor: '#4CAF50',
    color: 'white',
    border: 'none',
    borderRadius: '5px',
    cursor: 'pointer',
  },
  analysisContainer: {
    marginTop: '20px',
    padding: '15px',
    backgroundColor: '#f0f0f0',
    borderRadius: '5px',
  },
  sourceLink: {
    display: 'block',
    marginTop: '20px',
    color: '#666',
    textDecoration: 'none',
  }
};

function client() {
  createRoot(document.getElementById("root")).render(<App />);
}
if (typeof document !== "undefined") { client(); }

export default async function server(request: Request): Promise<Response> {
  if (request.method === 'POST' && new URL(request.url).pathname === '/analyze') {
    const { OpenAI } = await import("https://esm.town/v/std/openai");
    const openai = new OpenAI();
    
    try {
      const { image } = await request.json();
      
      const completion = await openai.chat.completions.create({
        model: "gpt-4o-mini",
        messages: [
          {
            role: "user",
            content: [
              { 
                type: "text", 
                text: "Describe this image in detail. What do you see? Provide context and interesting observations." 
              },
              { 
                type: "image_url", 
                image_url: { url: image } 
              }
            ]
          }
        ],
        max_tokens: 300
      });

      return new Response(
        completion.choices[0].message.content || "No description available", 
        { headers: { "Content-Type": "text/plain" } }
      );
    } catch (error) {
      return new Response(`Error: ${error}`, { status: 500 });
    }
  }

  return new Response(`
    <html>
      <head>
        <title>Image Analyzer</title>
        <meta name="viewport" content="width=device-width, initial-scale=1">
      </head>
      <body>
        <div id="root"></div>
        <script src="https://esm.town/v/std/catch"></script>
        <script type="module" src="${import.meta.url}"></script>
      </body>
    </html>
  `, {
    headers: { "Content-Type": "text/html" }
  });
}
