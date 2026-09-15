<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<meta name="theme-color" content="#111111">

<title>KING'S 2 BAR & RESTAURANT - Attendance</title>

<style>
* {
    box-sizing: border-box;
}

body {
    margin: 0;
    font-family: Arial, sans-serif;
    background: #f3f3f3;
    color: #222;
}

header {
    background: linear-gradient(135deg, #080808, #252525);
    color: white;
    text-align: center;
    padding: 22px 12px;
    border-bottom: 4px solid #d4af37;
}

header h1 {
    margin: 0;
    font-size: 22px;
    letter-spacing: .5px;
}

header p {
    margin: 7px 0 0;
    color: #d4af37;
    font-size: 13px;
}

.container {
    max-width: 1050px;
    margin: auto;
    padding: 15px;
}

.card {
    background: white;
    padding: 15px;
    margin-bottom: 15px;
    border-radius: 13px;
    box-shadow: 0 2px 9px rgba(0,0,0,.08);
}

.card h2,
.card h3 {
    margin-top: 0;
}

.date-row,
.form-row {
    display: flex;
    gap: 8px;
}

input {
    width: 100%;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 9px;
    font-size: 15px;
}

.date-row input,
.form-row input {
    flex: 1;
}

button {
    border: none;
    padding: 11px 14px;
    border-radius: 9px;
    font-weight: bold;
    cursor: pointer;
}

button:active {
    transform: scale(.97);
}

.gold {
    background: #d4af37;
    color: #111;
}

.dark {
    background: #111;
    color: white;
}

.green {
    background: #198754;
    color: white;
}

.red {
    background: #dc3545;
    color: white;
}

.orange {
    background: #e58f00;
    color: white;
}

.blue {
    background: #2563eb;
    color: white;
}

.gray {
    background: #eeeeee;
    color: #b42318;
}

.stats {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    margin-bottom: 15px;
}

.stat {
    background: white;
    padding: 15px 5px;
    text-align: center;
    border-radius: 13px;
    box-shadow: 0 2px 9px rgba(0,0,0,.08);
}

.stat strong {
    display: block;
    font-size: 27px;
}

.stat small {
    color: #666;
}

.present-number {
    color: #198754;
}

.absent-number {
    color: #dc3545;
}

.late-number {
    color: #e58f00;
}

.search {
    margin-bottom: 10px;
}

.staff {
    background: #fafafa;
    border: 1px solid #ddd;
    border-radius: 11px;
    padding: 13px;
    margin-top: 10px;
}

.staff-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 8px;
}

.staff-name {
    font-size: 17px;
    font-weight: bold;
}

.badge {
    padding: 5px 9px;
    border-radius: 20px;
    font-size: 11px;
    font-weight: bold;
}

.badge-present {
    background: #d9f5e3;
    color: #137333;
}

.badge-absent {
    background: #ffe0e0;
    color: #b42318;
}

.badge-late {
    background: #fff0c9;
    color: #9a6700;
}

.badge-pending {
    background: #eeeeee;
    color: #555;
}

.time {
    color: #666;
    font-size: 12px;
    margin: 9px 0;
}

.actions {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 6px;
}

.actions button {
    font-size: 12px;
}

.checkout {
    width: 100%;
    margin-top: 6px;
    background: #333;
    color: white;
}

.delete {
    width: 100%;
    margin-top: 6px;
}

.insight {
    background: #fff8df;
    border-left: 4px solid #d4af37;
    padding: 12px;
    border-radius: 8px;
    font-size: 13px;
    line-height: 1.6;
}

.report-buttons {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 8px;
}

#monthlySummary {
    margin-top: 12px;
    font-size: 13px;
}

.history {
    overflow-x: auto;
}

table {
    width: 100%;
    border-collapse: collapse;
    font-size: 12px;
}

th,
td {
    padding: 9px 7px;
    border-bottom: 1px solid #ddd;
    text-align: left;
    white-space: nowrap;
}

footer {
    text-align: center;
    color: #777;
    font-size: 11px;
    padding: 20px;
}

@media(max-width:600px) {

    header h1 {
        font-size: 19px;
    }

    .stats {
        grid-template-columns: repeat(2, 1fr);
    }

    .date-row,
    .form-row {
        flex-direction: column;
    }

    .report-buttons {
        grid-template-columns: 1fr;
    }
}
</style>
</head>

<body>

<header>
    <h1>👑 KING'S 2 BAR & RESTAURANT</h1>
    <p>Smart Daily Attendance Management</p>
</header>

<div class="container">

    <!-- DATE -->

    <div class="card">

        <h3>📅 Attendance Date</h3>

        <div class="date-row">

            <input
                type="date"
                id="attendanceDate"
            >

            <button
                class="gold"
                onclick="setToday()"
            >
                Today
            </button>

        </div>

    </div>


    <!-- DASHBOARD -->

    <div class="stats">

        <div class="stat">

            <strong id="totalStaff">
                0
            </strong>

            <small>
                Total Staff
            </small>

        </div>


        <div class="stat">

            <strong
                id="presentCount"
                class="present-number"
            >
                0
            </strong>

            <small>
                Present
            </small>

        </div>


        <div class="stat">

            <strong
                id="absentCount"
                class="absent-number"
            >
                0
            </strong>

            <small>
                Absent
            </small>

        </div>


        <div class="stat">

            <strong
                id="lateCount"
                class="late-number"
            >
                0
            </strong>

            <small>
                Late
            </small>

        </div>

    </div>


    <!-- INTELLIGENT INSIGHT -->

    <div class="card">

        <h3>🧠 Smart Attendance Insight</h3>

        <div
            class="insight"
            id="insight"
        >
            Add staff and mark attendance
            to see smart insights.
        </div>

    </div>


    <!-- ADD STAFF -->

    <div class="card">

        <h3>➕ Add Staff</h3>

        <div class="form-row">

            <input
                id="staffName"
                placeholder="Enter staff name"
            >

            <button
                class="dark"
                onclick="addStaff()"
            >
                Add Staff
            </button>

        </div>

    </div>


    <!-- STAFF -->

    <div class="card">

        <h3>👥 Staff Attendance</h3>

        <input
            class="search"
            id="search"
            placeholder="🔍 Search staff..."
            oninput="displayStaff()"
        >

        <div id="staffList"></div>

    </div>


    <!-- REPORT -->

    <div class="card">

        <h3>📊 Monthly Report</h3>

        <div class="report-buttons">

            <button
                class="dark"
                onclick="monthlyReport()"
            >
                View Summary
            </button>

            <button
                class="blue"
                onclick="exportCSV()"
            >
                Export CSV
            </button>

            <button
                class="red"
                onclick="clearToday()"
            >
                Clear Today
            </button>

        </div>

        <div id="monthlySummary"></div>

    </div>


    <!-- HISTORY -->

    <div class="card">

        <h3>📋 Attendance History</h3>

        <div class="history">

            <table>

                <thead>

                    <tr>

                        <th>Date</th>

                        <th>Staff</th>

                        <th>Status</th>

                        <th>Check-in</th>

                        <th>Check-out</th>

                    </tr>

                </thead>

                <tbody
                    id="historyTable"
                ></tbody>

            </table>

        </div>

    </div>

</div>


<footer>

    👑 KING'S 2 BAR & RESTAURANT

    <br>

    Smart Attendance System

</footer>


<script>

/* ==============================
   STORAGE
============================== */

const STAFF_KEY =
    "kings2_staff";

const ATTENDANCE_KEY =
    "kings2_attendance";


let staff =
    JSON.parse(
        localStorage.getItem(STAFF_KEY)
        || "[]"
    );


let attendance =
    JSON.parse(
        localStorage.getItem(ATTENDANCE_KEY)
        || "{}"
    );


/* ==============================
   DATE
============================== */

function getTodayDate() {

    const d = new Date();

    return (
        d.getFullYear()
        + "-"
        + String(
            d.getMonth() + 1
        ).padStart(2, "0")
        + "-"
        + String(
            d.getDate()
        ).padStart(2, "0")
    );

}


function setToday() {

    document.getElementById(
        "attendanceDate"
    ).value = getTodayDate();

    render();

}


/* ==============================
   TIME
============================== */

function getTime() {

    return new Date()
        .toLocaleTimeString(
            [],
            {
                hour: "2-digit",
                minute: "2-digit"
            }
        );

}


/* ==============================
   SAVE
============================== */

function saveData() {

    localStorage.setItem(
        STAFF_KEY,
        JSON.stringify(staff)
    );

    localStorage.setItem(
        ATTENDANCE_KEY,
        JSON.stringify(attendance)
    );

}


/* ==============================
   CURRENT DATE
============================== */

function selectedDate() {

    return document.getElementById(
        "attendanceDate"
    ).value;

}


/* ==============================
   DAY RECORD
============================== */

function getDayRecord() {

    const date =
        selectedDate();

    if (!attendance[date]) {

        attendance[date] = {};

    }

    return attendance[date];

}


/* ==============================
   ADD STAFF
============================== */

function addStaff() {

    const input =
        document.getElementById(
            "staffName"
        );

    const name =
        input.value.trim();


    if (!name) {

        alert(
            "Please enter staff name."
        );

        return;

    }


    const exists =
        staff.some(
            x =>
                x.toLowerCase()
                === name.toLowerCase()
        );


    if (exists) {

        alert(
            "This staff member already exists."
        );

        return;

    }


    staff.push(name);

    input.value = "";

    saveData();

    render();

}


/* ==============================
   MARK ATTENDANCE
============================== */

function markAttendance(
    name,
    status
) {

    const day =
        getDayRecord();


    if (!day[name]) {

        day[name] = {};

    }


    day[name].status =
        status;


    if (
        status === "present"
        ||
        status === "late"
    ) {

        if (!day[name].checkIn) {

            day[name].checkIn =
                getTime();

        }

    }


    if (
        status === "absent"
    ) {

        day[name].checkIn =
            "—";

        day[name].checkOut =
            "—";

    }


    saveData();

    render();

}


/* ==============================
   CHECK OUT
============================== */

function checkOut(name) {

    const day =
        getDayRecord();


    if (
        !day[name]
        ||
        (
            day[name].status !==
            "present"
            &&
            day[name].status !==
            "late"
        )
    ) {

        alert(
            "Mark Present or Late first."
        );

        return;

    }


    day[name].checkOut =
        getTime();


    saveData();

    render();

}


/* ==============================
   DELETE STAFF
============================== */

function deleteStaff(name) {

    if (
        !confirm(
            "Remove " +
            name +
            " from staff list?"
        )
    ) {

        return;

    }


    staff =
        staff.filter(
            x => x !== name
        );


    saveData();

    render();

}


/* ==============================
   DISPLAY STAFF
============================== */

function displayStaff() {

    const list =
        document.getElementById(
            "staffList"
        );


    const search =
        document.getElementById(
            "search"
        )
        .value
        .toLowerCase();


    const day =
        getDayRecord();


    const filtered =
        staff.filter(
            name =>
                name
                .toLowerCase()
                .includes(search)
        );


    if (!filtered.length) {

        list.innerHTML =
            `
            <p style="
                text-align:center;
                color:#777;
                padding:20px;
            ">
                No staff found.
            </p>
            `;

        return;

    }


    list.innerHTML =
        filtered
        .map(
            name => {

                const data =
                    day[name]
                    || {};


                const status =
                    data.status
                    || "pending";


                let label =
                    "Not Marked";


                if (
                    status ===
                    "present"
                )
                    label =
                        "Present";


                if (
                    status ===
                    "absent"
                )
                    label =
                        "Absent";


                if (
                    status ===
                    "late"
                )
                    label =
                        "Late";


                let badge =
                    "badge-pending";


                if (
                    status ===
                    "present"
                )
                    badge =
                        "badge-present";


                if (
                    status ===
                    "absent"
                )
                    badge =
                        "badge-absent";


                if (
                    status ===
                    "late"
                )
                    badge =
                        "badge-late";


                return `

                <div class="staff">

                    <div class="staff-top">

                        <span class="staff-name">

                            ${escapeHTML(name)}

                        </span>


                        <span
                            class="badge ${badge}"
                        >

                            ${label}

                        </span>

                    </div>


                    <div class="time">

                        Check-in:
                        ${data.checkIn || "—"}

                        &nbsp; | &nbsp;

                        Check-out:
                        ${data.checkOut || "—"}

                    </div>


                    <div class="actions">

                        <button
                            class="green"
                            onclick="markAttendance(
                                '${escapeJS(name)}',
                                'present'
                            )"
                        >
                            ✓ Present
                        </button>


                        <button
                            class="orange"
                            onclick="markAttendance(
                                '${escapeJS(name)}',
                                'late'
                            )"
                        >
                            ⏰ Late
                        </button>


                        <button
                            class="red"
                            onclick="markAttendance(
                                '${escapeJS(name)}',
                                'absent'
                            )"
                        >
                            ✕ Absent
                        </button>

                    </div>


                    <button
                        class="checkout"
                        onclick="checkOut(
                            '${escapeJS(name)}'
                        )"
                    >
                        🕐 Check-out
                    </button>


                    <button
                        class="delete"
                        onclick="deleteStaff(
                            '${escapeJS(name)}'
                        )"
                    >
                        Remove Staff
                    </button>

                </div>

                `;

            }
        )
        .join("");

}


/* ==============================
   DASHBOARD
============================== */

function updateStats() {

    const day =
        getDayRecord();


    let present = 0;
    let absent = 0;
    let late = 0;


    Object.values(day)
        .forEach(
            data => {

                if (
                    data.status ===
                    "present"
                )
                    present++;


                if (
                    data.status ===
                    "absent"
                )
                    absent++;


                if (
                    data.status ===
                    "late"
                )
                    late++;

            }
        );


    document.getElementById(
        "totalStaff"
    ).textContent =
        staff.length;


    document.getElementById(
        "presentCount"
    ).textContent =
        present;


    document.getElementById(
        "absentCount"
    ).textContent =
        absent;


    document.getElementById(
        "lateCount"
    ).textContent =
        late;

}


/* ==============================
   SMART INSIGHT
============================== */

function smartInsight() {

    const month =
        selectedDate()
        .substring(0, 7);


    let latePeople = {};
    let absentPeople = {};


    Object.keys(attendance)
        .forEach(
            date => {

                if (
                    !date.startsWith(month)
                )
                    return;


                Object.entries(
                    attendance[date]
                )
                .forEach(
                    ([name, data]) => {

                        if (
                            data.status ===
                            "late"
                        ) {

                            latePeople[name] =
                                (
                                    latePeople[name]
                                    || 0
                                ) + 1;

                        }


                        if (
                            data.status ===
                            "absent"
                        ) {

                            absentPeople[name] =
                                (
                                    absentPeople[name]
                                    || 0
                                ) + 1;

                        }

                    }
                );

            }
        );


    const day =
        getDayRecord();


    const present =
        Object.values(day)
        .filter(
            x =>
                x.status ===
                "present"
        ).length;


    const late =
        Object.values(day)
        .filter(
            x =>
                x.status ===
                "late"
        ).length;


    const absent =
        Object.values(day)
        .filter(
            x =>
                x.status ===
                "absent"
        ).length;


    let message =
        "Today: " +
        "<b>" +
        present +
        "</b> Present, " +
        "<b>" +
        late +
        "</b> Late, " +
        "<b>"
