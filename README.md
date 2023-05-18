# School-Projects

<html>
<head>

    <title>Hannah Montana Analysis Dashboard</title>

    <script type="text/javascript"
	    src="https://public.tableau.com/javascripts/api/tableau-2.min.js"></script>
    <script type="text/javascript"></script>

</head>

<body>

  <u><h1>Hannah Montana Analysis Dashboard</h1></u>

    <button id = "exportPDF">Generate PDF</button>
    <button id = "exportImage">Generate Image</button>
    <br><br>

    <div id="vizContainer"></div>

    <script src="./app.js"></script>

</body>

</html>

console.log('Is this working?');

let viz;

//Add Share Link to Tableau Public in here
const url = "https://public.tableau.com/views/HannahMontanaAnalysisDashboard/Dashboard?:language=en-US&:display_count=n&:origin=viz_share_link";

const vizContainer = document.getElementById('vizContainer');
const options = {
    
    height: 900,
    width: 1666,
    onFirstInteraction: function() {
        workbook = viz.getWorkbook();
        activeSheet = workbook.getActiveSheet();
        console.log("My dashboard is interactive");
    }
};

//create a function to generate the viz element
function initViz() {
    console.log('Executing the initViz function!');
    viz = new tableau.Viz(vizContainer, url, options);
}

// run the initViz function when the page loads
document.addEventListener("DOMContentLoaded", initViz);

const exportPDF = document.getElementById('exportPDF');
const exportImage = document.getElementById('exportImage');


//click on the pdf button to generate pdf of dashboard
function generatePDF() {
    viz.showExportPDFDialog()
}

exportPDF.addEventListener("click", function () {
    generatePDF();
  });

//click on image to generate image of dashboard
function generateImage() {
    viz.showExportImageDialog()
}

exportImage.addEventListener("click", function () {
    generateImage();
  });
