## Comportamiento


¿Qué es la comunicación en las organizaciones?
La comunicación en las organizaciones tiene que ver con la difusión de mensajes con el fin de transmitir, puertas adentro, los logros y requerimientos a los miembros que la conforman. Aunque también se comunica puertas afuera y, en este caso, sirve para que la sociedad también conozca cuales son las misiones, visiones y metas de cualquier organización.
En general, el encargado de la comunicación organizacional es el departamento de Recursos humanos. Vale destacar que no todos los mensajes son para todos los colaboradores, así como tampoco se comunican de igual manera en todos los estratos de la organización. Los mensajes varían de acuerdo nivel de la pirámide al que se quiere comunicar: no es lo mismo para quienes ocupan cargos jerárquicos que para quienes están en la base.
Importancia de la comunicación en las organizaciones
La comunicación organizacional permite conocer el desempeño de los departamentos.
La comunicación en las organizaciones es trascendental. El alcance de los objetivos de la firma, en buena parte, depende de cómo sea la comunicación.
A través de ella, los colaboradores se mantienen al tanto de cuáles son los requerimientos y los objetivos alcanzados. Al mismo tiempo, la comunicación les permite conocer a los empleados cómo fue su evolución dentro de la firma y cómo han sido los desempeños de cada uno de los departamentos.
Puertas afuera, la comunicación organizacional es la herramienta que ayuda a las compañías a elaborar la imagen que quieren que la sociedad tenga de ellas mismas.

<div>Teachable Machine Image Model</div>
<button type="button" onclick="init()">Start</button>
<div id="webcam-container"></div>
<div id="label-container"></div>
<script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.3.1/dist/tf.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@teachablemachine/image@0.8/dist/teachablemachine-image.min.js"></script>
<script type="text/javascript">
    // More API functions here:
    // https://github.com/googlecreativelab/teachablemachine-community/tree/master/libraries/image

    // the link to your model provided by Teachable Machine export panel
    const URL = "./my_model/";

    let model, webcam, labelContainer, maxPredictions;

    // Load the image model and setup the webcam
    async function init() {
        const modelURL = URL + "model.json";
        const metadataURL = URL + "metadata.json";

        // load the model and metadata
        // Refer to tmImage.loadFromFiles() in the API to support files from a file picker
        // or files from your local hard drive
        // Note: the pose library adds "tmImage" object to your window (window.tmImage)
        model = await tmImage.load(modelURL, metadataURL);
        maxPredictions = model.getTotalClasses();

        // Convenience function to setup a webcam
        const flip = true; // whether to flip the webcam
        webcam = new tmImage.Webcam(200, 200, flip); // width, height, flip
        await webcam.setup(); // request access to the webcam
        await webcam.play();
        window.requestAnimationFrame(loop);

        // append elements to the DOM
        document.getElementById("webcam-container").appendChild(webcam.canvas);
        labelContainer = document.getElementById("label-container");
        for (let i = 0; i < maxPredictions; i++) { // and class labels
            labelContainer.appendChild(document.createElement("div"));
        }
    }

    async function loop() {
        webcam.update(); // update the webcam frame
        await predict();
        window.requestAnimationFrame(loop);
    }

    // run the webcam image through the image model
    async function predict() {
        // predict can take in an image, video or canvas html element
        const prediction = await model.predict(webcam.canvas);
        for (let i = 0; i < maxPredictions; i++) {
            const classPrediction =
                prediction[i].className + ": " + prediction[i].probability.toFixed(2);
            labelContainer.childNodes[i].innerHTML = classPrediction;
        }
    }
</script>








<script src="https://www.gstatic.com/dialogflow-console/fast/messenger/bootstrap.js?v=1"></script>
<df-messenger
  intent="WELCOME"
  chat-title="mascarilla"
  agent-id="d98d4c03-9631-4df4-a602-9683ced68e1b"
  language-code="en"
></df-messenger>


