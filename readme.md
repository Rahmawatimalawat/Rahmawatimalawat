Nama : Andira Azzahra
NIM : 1313619006

Question 1
Langkah pertama adalah mengisi obsVars dengan membuat obsVar = OBS_VAR_TEMPLATE % obsPos lalu meng-append obsVar kedalam obsVars. Selanjutnya mengisi 'edges' dengan setiap edge di Bayes Net dengan tuple (dari, ke). Meletakkan setiap 'variableDomainsDict[variable] = values' dimana valuesnya adalah sebuah set dari tugas yg memungkinkan untuk 'variable'.
Question 2
Pada soal ini membahas tentang kemungkinan bayes net dan diharuskan mengisi CPT yang nantinya memberikan kemungkinan yang lebih dulu pada posisi variabel y. Jadi yang lebih dulu adalah( { Y_POS_VAR: BOTH_TOP_VAL}, PROB_BOTH_TOP), lalu yg kedua adalah ({Y_POS_VAR: BOTH_BOTTOM_VAL}, PROB_BOTH_BOTTOM) lalu yang ke 3 ({Y_POS_VAR: LEFT_TOP_VAL}, PROB_ONLY_LEFT_TOP) dan yang terakhir ({Y_POS_VAR: LEFT_BOTTOM_VAL}, PROB_ONLY_LEFT_BOTTOM).
Question 3
Pertama-tama mengisi variabel condition selanjutnya mendapatkan variable domains dengan mengisinya dengan factor. Langkah berikutnya mendapatkan variabel uncondition, lalu cek adakah condition di dalam uncodition? Jika ada saya akan menghapus condition tersebut. Saya membuat factor baru dengan nama variabel 'fctr'. newAllPossibleDict = fctr. Lalu membuat kemungkinan 'fctr' menjadi 1(pasti terjadi). Selanjutnya perhitungkan kemungkinan terbaru.
Question 4
Mendapatkan variabel condition dengan meng-append temporary yang merupakan index pada perulangan di setsOfConditioned selanjutnya mendapatkan variable domains dengan mengisinya dengan factor.variableDomainsDict. selanjutnya mendapatkan variabel uncondition. Lalu eliminasi variabel dari uncondition, dengan value dari ‘eliminationVariable’. Lalu setelahnya membuat factor baru dengan nama variabel ‘fctr’. Lalu membuat kemungkinan faktor barunya menjadi 0(tidak akan terjadi). Lalu langkah terakhir menghitung kemungkinan baru.

Question 5
Mendapatkan variabel condition dengan meng-append temporary yang merupakan index pada perulangan di setsOfConditioned. Lalu mendapatkan variabel uncondition dengan meng-append temporary yang merupakan index pada perulangan di setsOfUnconditioned. Langkah selanjutnya mendapatkan kemungkinan dari domains dari kemungkinan assignment dicts. Lalu melakukan pengecekan, jika variabel hanya memiliki satu entry di domain dict, kita dapat mengasumsikan bahwa variabel yang ditugaskan sebagai fakta/keterangan lalu memindahkan variabel ke list condition.  Lalu setelahnya membuat factor baru dengan nama variabel ‘fctr’. Lalu membuat kemungkinan faktor barunya menjadi 0(tidak akan terjadi). Setelahnya menghitung total value dari kemungkinan AllPossibleAssignmentDicts. Lalu langkah terakhir menghitung kemungkinan baru.

