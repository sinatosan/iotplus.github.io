<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width,initial-scale=1" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>SmartSept Config</title>
    <style>
        body {
            margin: 0;
            font-family: Helvetica, sans-serif;
            background-color: #ebeef4;
        }

        * {
            box-sizing: border-box;
        }

        .header__title1 {
            color: #f4511e;
            margin: 10px 0 0 10px;
        }

        .header__title2 {
            color: #b0bebe;
            margin: 0 0 20px 10px;
            font-size: 22px;
        }

        .container {
            display: grid;
            width: 95%;
            margin: auto;
            background-color: #fff;
            border-radius: 5px;
            padding: 40px 20px;
            margin-bottom: 30px;
        }

        form.container {
            gap: 100px;
        }

        .fieldset__legend {
            font-weight: 800;
            font-size: 20px;
            color: #627183;
        }

        .field__label {
            color: #627183;
        }

        .form__submit {
            height: 40px;
            font-size: medium;
            background: #f4511e;
            color: #fff;
            border: none;
            border-radius: 4px;
            cursor: pointer;
        }

        .field__input {
            border: 1px solid rgba(56, 62, 77, 0.4);
            border-radius: 4px;
            height: 40px;
            background-color: rgba(56, 62, 77, 0.03);
            padding-left: 11px;
            outline: 0;
            font-weight: 500;
            margin-top: 4px;
            font-size: 16px;
            font-weight: 500;
        }

        .fieldset__field__oneCol {
            display: flex;
            flex-direction: column;
            flex: 1;
        }

        .fieldset {
            display: grid;
            gap: 40px;
        }

        .fieldset__fields {
            display: grid;
            gap: 20px;
        }

        @media (min-width: 576px) {
            .container {
                width: 90%;
            }

            body {
                padding-bottom: 100px;
            }
        }

        @media (min-width: 768px) {
            .container {
                width: 80%;
                padding: 40px;
            }
        }

        @media (min-width: 992px) {
            .container {
                width: 60%;
            }
        }

        @media (min-width: 1200px) {
            .container {
                width: 50%;
            }
        }
    </style>
</head>

<body>
    <header class="header">
        <div class="header__title-group">
            <h1 class="header__title1">DISPENSER</h1>
            <h1 class="header__title2">Configuration</h1>
        </div>
    </header>
    <div class="container">
        <div style="display: flex">
            <p class="field__label" style="margin-right: 5px">MAC Address:</p>
            <p id="mac"></p>
        </div>
        <div style="display: flex">
            <p class="field__label" style="margin-right: 5px">Firmware Version:</p>
            <p id="firmwareVersion"></p>
        </div>
        <div style="display: flex">
            <p class="field__label" style="margin-right: 5px">Hardware Version:</p>
            <p id="hardwareVersion"></p>
        </div>
    </div>
    <form class="container" method="POST" action="/config">
        <div class="fieldset">
            <label class="fieldset__legend" for="externalAp">Network</label>
            <div class="fieldset__fields" id="externalAp">
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="externalApSSID">SSID</label><input type="text"
                        name="external-ap-ssid" id="externalApSSID" class="field__input" placeholder="SSID" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="externalApPass">Password</label><input type="password"
                        name="external-ap-pass" id="externalApPass" class="field__input" placeholder="******" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label">Show Password
                        <input type="checkbox" onclick="toggleShow('externalApPass')">
                    </label>
                </div>
            </div>
        </div>
        <div class="fieldset">
            <label class="fieldset__legend" for="customerInfo">Customer Info</label>
            <div class="fieldset__fields" id="customerInfo">
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="hostIP">Host</label><input type="text" name="host" id="hostIP"
                        class="field__input" placeholder="IP" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="healthCenterId">Health Center ID</label><input type="text"
                        name="health-center" id="healthCenterId" class="field__input" placeholder="ID" />
                </div>
            </div>
        </div>
        <div class="fieldset">
            <label class="fieldset__legend" for="internalAp">Internal Access Point</label>
            <div class="fieldset__fields" id="internalAp">
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="internalApSSID">SSID</label><input type="text"
                        name="internal-ap-ssid" id="internalApSSID" class="field__input" placeholder="SSID" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="internalApPass">Password</label><input type="password"
                        name="internal-ap-pass" id="internalApPass" class="field__input" placeholder="******" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label">Show Password
                        <input type="checkbox" onclick="toggleShow('internalApPass')">
                    </label>
                </div>
            </div>
        </div>
        <div class="fieldset">
            <label class="fieldset__legend" for="accessControl">Config Panel</label>
            <div class="fieldset__fields" id="accessControl">
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="adminUsername">Username</label><input type="text"
                        name="admin-username" id="adminUsername" class="field__input" placeholder="Usename" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label" for="adminPassword">Password</label><input type="password"
                        name="admin-Password" id="adminPassword" class="field__input" placeholder="******" />
                </div>
                <div class="fieldset__field__oneCol">
                    <label class="field__label">Show Password
                        <input type="checkbox" onclick="toggleShow('adminPassword')">
                    </label>
                </div>
            </div>
        </div>
        <button class="form__submit" type="submit" name="form-submit">
            Save
        </button>
    </form>
    <script>
        var xhttp = new XMLHttpRequest();
        (xhttp.onreadystatechange = function () {
            if (4 == this.readyState && 200 == this.status) {
                var e = JSON.parse(xhttp.responseText);
                (document.getElementById("mac").innerHTML = e.mac),
                    (document.getElementById("firmwareVersion").innerHTML =
                        e.firmwareVersion),
                    (document.getElementById("hardwareVersion").innerHTML =
                        e.hardwareVersion),
                    (document.getElementById("internalApSSID").value =
                        e.internalApSSID),
                    (document.getElementById("internalApPass").value =
                        e.internalApPass),
                    (document.getElementById("externalApSSID").value =
                        e.externalApSSID),
                    (document.getElementById("externalApPass").value =
                        e.externalApPass),
                    (document.getElementById("adminUsername").value = e.adminUsername),
                    (document.getElementById("adminPassword").value = e.adminPassword),
                    (document.getElementById("hostIP").value = e.hostIP),
                    (document.getElementById("healthCenterId").value =
                        e.healthCenterId);
            }
        }),
            xhttp.open("GET", "/data/config"),
            xhttp.send();

        function toggleShow(id) {
            var x = document.getElementById(id);
            if (x.type === "password") {
                x.type = "text";
            } else {
                x.type = "password";
            }
        }
    </script>
</body>

</html>
