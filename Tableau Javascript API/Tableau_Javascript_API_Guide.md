
<b><h3>Tableau Javascript API</h3></b>
<hr/>
JS API is used to integrate tableau dashboard to your web application.

If user want to see visualizations into there website then JS API is good option.

Tableau provide an way to interact with tableau dashboard/story/view by embeding it to any application.

JS API allow visualizations from tableau server, tableau public and tableau cloud in web applications.
User can interact with tableau dashboard by using filter,parameter,mark selection events.

JS API provide many inbuild functions like functions exporting workbook as Crosstab,Powerpoint,Image,etc.
Also it provide functions to getData from view, to getFiltered values, to do Undo Redo actions and many more we will look  it in depth with this article.

Tableau JS API public link - https://public.tableau.com/javascripts/api/tableau-version.min.js

Tableau JS API cloud link - https://online.tableau.com/javascripts/api/tableau-version.min.js

Second needed thing is initialization function  "initViz()". This function will contain a Viz object which is neccessary to initialize api as api uses an object model.

Here is Sample Code To embed tableau dashboard into web page

<html>
<head>
    <title>Tableau Embed</title>

    <script type="text/javascript" src="https://public.tableau.com/javascripts/api/tableau-2.min.js"></script>
    <script type="text/javascript">
        function initViz() {
            var containerDiv = document.getElementById("vizContainer"),
                url = "https://public.tableau.com/views/SalesPerformanceDashboard_16697086953410/SalesPerformance?:language=en-US&publish=yes&:display_count=n&:origin=viz_share_link",
                options = {
                    hideTabs: true,
                    onFirstInteractive: function () {
                     
                    }
                };
            //Viz initialization
            var viz = new tableau.Viz(containerDiv, url, options);
        }
    </script>
</head>

<body onload="initViz();">
    <div id="vizContainer" style="width:700px; height:700px;"></div>
</body>

</html>

