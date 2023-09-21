# WORKSHEET_4
**#Index.Html**

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<style>
    table {
        width: 90%;
        margin:auto ;
        height: 33rem;
        text-align : center;
        font-size: large;
        background:#f9c3d6;
        padding: 1px;
        color:black;
        border: 2px solid blue;
    }
    h1{
        text-align: center;
    }
    .eee{
        display: none;
    }
    button{
       text-align: center;
       justify-content: space-between;
       width: 10rem;
       height: 2rem;
       background-color:deepskyblue;
       cursor: pointer;
    }
    
    .btn1{
        margin-left: 32rem;
        margin-top: 1rem;
    }
</style>
<body>
    <h1> Employee Salary Table.</h1>
    <table border="1 solid black">
        <tbody>
            <tr>
                <th>Name</th>
                <th> UID </th>
                <th>City</th>
                <th>Job role</th>
                <th>Salary</th>
            </tr>
            <tr>
                <td> Navneet </td>
                <td> 20149 </td>
                <td>Bettiah</td>
                <td> Developer </td>
                <td>
                    <input type="text" id="emp1" class="emp" />
                </td>
            </tr>

            <tr>
                <td>Aryan </td>
                <td> 20145 </td>
                <td> Lucknow </td>
                <td> Programmer </td>
                <td>
                    <input type="text" id="emp2" class="emp" />
                </td>
            </tr>

            <tr>
                <td>Pushpam</td>
                <td>20132</td>
                <td>Madhubani</td>
                <td>Analyst</td>
                <td>
                    <input type="text" id="emp3" class="emp" />
                </td>
            </tr>
            <tr>
                <td> Sachin </td>
                <td>20564</td>
                <td> Gaya </td>
                <td> Coder </td>
                <td>
                    <input type="text" id="emp4" class="emp" />
                </td>
            </tr>
            <tr>
                <td> Anand </td>
                <td>20558</td>
                <td> Chhapra </td>
                <td> Developer </td>
                <td>
                    <input type="text" id="emp5" class="emp" />
                </td>
            </tr>
            <tr>
                <td> Pushpdip </td>
                <td>20149</td>
                <td> Bihar </td>
                <td> Coder </td>
                <td>
                    <input type="text" id="emp6" class="emp" />
                </td>
            </tr>
        </tbody>
    </table>

    <button class="btn1" onclick="show()">show</button>
    <!-- <button class="btn2" onclick="hide()">Hide</button> -->
    <button class="btn1" onclick="tsalar()">Total Sallary</button>
    <!-- <h1><input type="number" id="totalsalary"/> </h1> -->

  </div>

  <script>
   let data1 = 104500;   //dev
    let data2 = 95000;   //pro
    let data3 = 85000;   //ana
    let data4 = 80000;   //coder
    let data5 = 90000;
    function show() {
      let emp1 = (document.getElementById("emp1").value = data1);
      let emp2 = (document.getElementById("emp2").value = data2);
      let emp3 = (document.getElementById("emp3").value = data3);
      let emp4 = (document.getElementById("emp4").value = data4);
      let emp5 = (document.getElementById("emp5").value = data1);
      let emp6 = (document.getElementById("emp6").value = data4);
    }
    function tsalar(){
        let total=data1+data2+data3+data4+data5;
        alert(total);
        document.getElementById("totalsalary").value = total;

    }
  </script>


</body>

</html>

**#Index.js**
const fs = require('fs').promises;
const fs1 = require('fs');
const http = require('http');


async function readFile(filePath){
    try{
        const data = await fs.readFile(filePath);
        console.log(data.toString());
        const data1 = data.toString();

        fs.writeFile('newFile.html', data1)
    }catch(error){
        console.log("Error", error, "in file ", filePath );
    }
}
readFile('index.html');
http.createServer(function (req, res){
    fs1.readFile('newFile.html', function(err, data) {
        if (err) {
            res.writeHead(404);
          console.error('Error reading HTML file:', err);
          res.end();
        }
        else {
            res.writeHead(200, {'Content-type': 'text/html'})
            res.write(data);
            res.write("<h1>Total Salary = 729000</h1>");
        }
    });

}).listen(8080);



