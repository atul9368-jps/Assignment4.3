Student marksheet tabel
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 4.3 - Student Marks Table</title>
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <!-- Google Fonts: Inter -->
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      font-family: 'Inter', sans-serif;
    }
    @media print {
      .no-print {
        display: none !important;
      }
      body {
        background-color: white !important;
        padding: 0 !important;
      }
      .print-shadow-none {
        box-shadow: none !important;
        border: none !important;
      }
    }
  </style>
</head>
<body class="bg-slate-100 min-h-screen py-8 px-4 sm:px-6 lg:px-8">

  <div class="max-w-5xl mx-auto space-y-6">

    <!-- Top Action Bar / Header -->
    <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4 no-print">
      <div>
        <div class="inline-flex items-center space-x-2 bg-blue-100 text-blue-700 px-3 py-1 rounded-full text-xs font-semibold mb-1">
          <span>Assignment 4.3</span>
        </div>
        <h1 class="text-2xl sm:text-3xl font-bold text-slate-800">Academic Marksheet Dashboard</h1>
        <p class="text-xs sm:text-sm text-slate-500">Academic Evaluation Record — Semester I</p>
      </div>

      <div class="flex items-center space-x-3">
        <!-- Search Input -->
        <div class="relative">
          <input 
            type="text" 
            id="searchInput" 
            placeholder="Search student..." 
            class="pl-9 pr-4 py-2 rounded-lg border border-slate-300 focus:ring-2 focus:ring-blue-500 focus:border-blue-500 text-xs sm:text-sm outline-none w-44 sm:w-64 bg-white shadow-sm transition"
          >
          <svg class="w-4 h-4 text-slate-400 absolute left-3 top-2.5" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
          </svg>
        </div>

        <!-- Print Button -->
        <button 
          onclick="window.print()" 
          class="inline-flex items-center space-x-2 bg-slate-800 hover:bg-slate-900 active:scale-95 text-white text-xs sm:text-sm font-semibold px-4 py-2.5 rounded-lg shadow transition cursor-pointer"
        >
          <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 17h2a2 2 0 002-2v-4a2 2 0 00-2-2H5a2 2 0 00-2 2v4a2 2 0 002 2h2m2 4h6a2 2 0 002-2v-4a2 2 0 00-2-2H9a2 2 0 00-2 2v4a2 2 0 002 2zm8-12V5a2 2 0 00-2-2H9a2 2 0 00-2 2v4h10z"></path>
          </svg>
          <span class="hidden sm:inline">Print Marksheet</span>
        </button>
      </div>
    </div>

    <!-- Main Table Container -->
    <div class="bg-white rounded-2xl shadow-xl border border-slate-200/80 overflow-hidden print-shadow-none">
      
      <div class="overflow-x-auto">
        <!-- Table Element -->
        <table class="w-full text-left border-collapse" id="marksTable">
          
          <!-- Caption Requirement -->
          <caption class="p-4 sm:p-5 text-left bg-gradient-to-r from-blue-600 via-indigo-600 to-violet-600 text-white font-semibold text-sm sm:text-base tracking-wide border-b border-indigo-700">
            <div class="flex items-center justify-between">
              <span class="flex items-center space-x-2">
                <svg class="w-5 h-5 text-blue-200" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12h6m-6 4h6m2 5H7a2 2 0 01-2-2V5a2 2 0 012-2h5.586a1 1 0 01.707.293l5.414 5.414a1 1 0 01.293.707V19a2 2 0 01-2 2z"></path>
                </svg>
                <span>Department of Computer Science — Student Performance Report</span>
              </span>
              <span class="text-xs font-normal text-blue-100 hidden sm:inline">Academic Session: 2026</span>
            </div>
          </caption>

          <!-- <thead> Section -->
          <thead class="bg-slate-800 text-slate-200 uppercase text-[11px] sm:text-xs tracking-wider border-b border-slate-700">
            <tr>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold">Roll No</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold">Student Name</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold text-center">Mathematics</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold text-center">Physics</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold text-center">Computer Science</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold text-center bg-slate-900/50">Total Marks</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold text-center">Grade</th>
              <th scope="col" class="py-3.5 px-4 sm:px-6 font-semibold text-center">Status</th>
            </tr>
          </thead>

          <!-- <tbody> Section -->
          <tbody class="divide-y divide-slate-100 text-xs sm:text-sm text-slate-700" id="studentBody">
            
            <!-- Student 1 -->
            <tr class="hover:bg-blue-50/60 transition-colors odd:bg-white even:bg-slate-50/50">
              <td class="py-4 px-4 sm:px-6 font-medium text-slate-500">CS-101</td>
              <td class="py-4 px-4 sm:px-6 font-semibold text-slate-900">Alex Johnson</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">92</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">88</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">95</td>
              <td class="py-4 px-4 sm:px-6 text-center font-bold text-blue-700 bg-slate-50/80">275 / 300</td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-semibold bg-emerald-100 text-emerald-800 border border-emerald-200">A+</span>
              </td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2 py-0.5 rounded text-xs font-semibold bg-emerald-50 text-emerald-700 border border-emerald-200">PASS</span>
              </td>
            </tr>

            <!-- Student 2 -->
            <tr class="hover:bg-blue-50/60 transition-colors odd:bg-white even:bg-slate-50/50">
              <td class="py-4 px-4 sm:px-6 font-medium text-slate-500">CS-102</td>
              <td class="py-4 px-4 sm:px-6 font-semibold text-slate-900">Sophia Martinez</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">78</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">82</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">89</td>
              <td class="py-4 px-4 sm:px-6 text-center font-bold text-blue-700 bg-slate-50/80">249 / 300</td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-semibold bg-blue-100 text-blue-800 border border-blue-200">A</span>
              </td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2 py-0.5 rounded text-xs font-semibold bg-emerald-50 text-emerald-700 border border-emerald-200">PASS</span>
              </td>
            </tr>

            <!-- Student 3 -->
            <tr class="hover:bg-blue-50/60 transition-colors odd:bg-white even:bg-slate-50/50">
              <td class="py-4 px-4 sm:px-6 font-medium text-slate-500">CS-103</td>
              <td class="py-4 px-4 sm:px-6 font-semibold text-slate-900">Liam Williams</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">64</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">70</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">68</td>
              <td class="py-4 px-4 sm:px-6 text-center font-bold text-blue-700 bg-slate-50/80">202 / 300</td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-semibold bg-amber-100 text-amber-800 border border-amber-200">B</span>
              </td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2 py-0.5 rounded text-xs font-semibold bg-emerald-50 text-emerald-700 border border-emerald-200">PASS</span>
              </td>
            </tr>

            <!-- Student 4 -->
            <tr class="hover:bg-blue-50/60 transition-colors odd:bg-white even:bg-slate-50/50">
              <td class="py-4 px-4 sm:px-6 font-medium text-slate-500">CS-104</td>
              <td class="py-4 px-4 sm:px-6 font-semibold text-slate-900">Emma Brown</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">85</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">91</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">94</td>
              <td class="py-4 px-4 sm:px-6 text-center font-bold text-blue-700 bg-slate-50/80">270 / 300</td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-semibold bg-emerald-100 text-emerald-800 border border-emerald-200">A+</span>
              </td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2 py-0.5 rounded text-xs font-semibold bg-emerald-50 text-emerald-700 border border-emerald-200">PASS</span>
              </td>
            </tr>

            <!-- Student 5 -->
            <tr class="hover:bg-blue-50/60 transition-colors odd:bg-white even:bg-slate-50/50">
              <td class="py-4 px-4 sm:px-6 font-medium text-slate-500">CS-105</td>
              <td class="py-4 px-4 sm:px-6 font-semibold text-slate-900">Noah Miller</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium text-rose-600 font-semibold">38</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">52</td>
              <td class="py-4 px-4 sm:px-6 text-center font-medium">60</td>
              <td class="py-4 px-4 sm:px-6 text-center font-bold text-blue-700 bg-slate-50/80">150 / 300</td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2.5 py-0.5 rounded-full text-xs font-semibold bg-rose-100 text-rose-800 border border-rose-200">C</span>
              </td>
              <td class="py-4 px-4 sm:px-6 text-center">
                <span class="inline-flex items-center px-2 py-0.5 rounded text-xs font-semibold bg-rose-50 text-rose-700 border border-rose-200">RE-APPEAR</span>
              </td>
            </tr>

          </tbody>

          <!-- <tfoot> Section (Utilizing colspan for Average and Summary Statistics) -->
          <tfoot class="bg-slate-900 text-slate-200 text-xs sm:text-sm font-semibold border-t-2 border-slate-700">
            <!-- Row 1: Subject Averages -->
            <tr>
              <td colspan="2" class="py-3.5 px-4 sm:px-6 text-right uppercase tracking-wider text-slate-400 font-bold">
                Subject Average Marks:
              </td>
              <td class="py-3.5 px-4 sm:px-6 text-center text-blue-300 font-bold">71.4</td>
              <td class="py-3.5 px-4 sm:px-6 text-center text-blue-300 font-bold">76.6</td>
              <td class="py-3.5 px-4 sm:px-6 text-center text-blue-300 font-bold">81.2</td>
              <td colspan="3" class="py-3.5 px-4 sm:px-6 text-center text-slate-400">Max Score per Subject: 100</td>
            </tr>

            <!-- Row 2: Overall Class Summary -->
            <tr class="bg-slate-950 border-t border-slate-800">
              <td colspan="5" class="py-4 px-4 sm:px-6 text-right uppercase tracking-wider text-slate-300 font-bold">
                Overall Class Average Performance:
              </td>
              <td colspan="3" class="py-4 px-4 sm:px-6 text-center text-emerald-400 font-extrabold text-sm sm:text-base">
                229.2 / 300 (76.4%)
              </td>
            </tr>
          </tfoot>

        </table>
      </div>

    </div>

    <!-- Quick Insights Footer Cards -->
    <div class="grid grid-cols-1 sm:grid-cols-3 gap-4 no-print pt-2">
      <div class="bg-white p-4 rounded-xl border border-slate-200/70 shadow-sm flex items-center space-x-3">
        <div class="p-3 bg-blue-100 rounded-lg text-blue-600">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 20h5v-2a3 3 0 00-5.356-1.857M17 20H7m10 0v-2c0-.656-.126-1.283-.356-1.857M7 20H2v-2a3 3 0 015.356-1.857M7 20v-2c0-.656.126-1.283.356-1.857m0 0a5.002 5.002 0 019.288 0M15 7a3 3 0 11-6 0 3 3 0 016 0zm6 3a2 2 0 11-4 0 2 2 0 014 0zM7 10a2 2 0 11-4 0 2 2 0 014 0z"></path>
          </svg>
        </div>
        <div>
          <p class="text-xs font-semibold text-slate-400 uppercase">Total Students</p>
          <p class="text-xl font-bold text-slate-800">5 Enrolled</p>
        </div>
      </div>

      <div class="bg-white p-4 rounded-xl border border-slate-200/70 shadow-sm flex items-center space-x-3">
        <div class="p-3 bg-emerald-100 rounded-lg text-emerald-600">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z"></path>
          </svg>
        </div>
        <div>
          <p class="text-xs font-semibold text-slate-400 uppercase">Pass Rate</p>
          <p class="text-xl font-bold text-slate-800">80.0% (4/5)</p>
        </div>
      </div>

      <div class="bg-white p-4 rounded-xl border border-slate-200/70 shadow-sm flex items-center space-x-3">
        <div class="p-3 bg-indigo-100 rounded-lg text-indigo-600">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 3v4M3 5h4M6 17v4m-2-2h4m5-16l2.286 6.857L21 12l-5.714 2.143L13 21l-2.286-6.857L5 12l5.714-2.143L13 3z"></path>
          </svg>
        </div>
        <div>
          <p class="text-xs font-semibold text-slate-400 uppercase">Top Performer</p>
          <p class="text-xl font-bold text-slate-800">Alex Johnson (91.6%)</p>
        </div>
      </div>
    </div>

  </div>

  <!-- Interactive Search JavaScript -->
  <script>
    document.addEventListener('DOMContentLoaded', () => {
      const searchInput = document.getElementById('searchInput');
      const tableRows = document.querySelectorAll('#studentBody tr');

      searchInput.addEventListener('input', (e) => {
        const query = e.target.value.toLowerCase().trim();

        tableRows.forEach(row => {
          const text = row.textContent.toLowerCase();
          if (text.includes(query)) {
            row.style.display = '';
          } else {
            row.style.display = 'none';
          }
        });
      });
    });
  </script>
</body>
</html>