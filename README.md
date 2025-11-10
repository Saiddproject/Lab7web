# Lab7web
Nama  : Muhammad Said Abimanyu

Nim   : 312410145 

Kelas : Ti.24.A1

# 📑Hasil Tugas yang sudah di buat
# Codingan awal 
```php
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tugas PHP Dasar</title>
</head>
<body>
<div class="container">
    <h2>Form Biodata dan Gaji</h2>
    <form method="POST">
        <label>Nama Lengkap:</label>
        <input type="text" name="nama" required><br><br>

        <label>Tanggal Lahir:</label>
        <input type="date" name="tgl_lahir" required><br><br>

        <label>Pekerjaan:</label>
        <select name="pekerjaan" required>
            <option value="">-- Pilih Pekerjaan --</option>
            <option value="Programmer">Programmer</option>
            <option value="Desainer">Desainer</option>
            <option value="Guru">Guru</option>
            <option value="Dokter">Dokter</option>
            <option value="Mahasiswa">Mahasiswa</option>
        </select><br><br>

        <input type="submit" name="submit" value="Tampilkan">
    </form>

    <?php
    $nama = "";
    $tgl_lahir = "";
    $pekerjaan = "";
    $umur = "-";
    $gaji_display = "-";
    
    if (isset($_POST['submit'])) {
        $nama = $_POST['nama'];
        $tgl_lahir = $_POST['tgl_lahir'];
        $pekerjaan = $_POST['pekerjaan'];

        $lahir = new DateTime($tgl_lahir);
        $hari_ini = new DateTime();
        
        if ($lahir > $hari_ini) {
            $umur = 0; 
        } else {
            $selisih = $hari_ini->diff($lahir);
            $umur = $selisih->y;
        }

        $gaji = 0;
        switch ($pekerjaan) {
            case "Programmer":
                $gaji = 12000000;
                break;
            case "Desainer":
                $gaji = 8500000;
                break;
            case "Guru":
                $gaji = 6500000;
                break;
            case "Dokter":
                $gaji = 17000000;
                break;
            case "Mahasiswa":
                $gaji = 500000; 
                break;
            default:
                $gaji = 1000000; 
                break;
        }
        
        $gaji_display = "Rp " . number_format($gaji, 0, ',', '.');
    
        echo "<hr><h3>Hasil Data:</h3>";
        echo "Nama: <b>$nama</b><br>";
        echo "Tanggal Lahir: <b>" . date('d-m-Y', strtotime($tgl_lahir)) . "</b><br>";
        echo "Umur: <b>$umur tahun</b><br>";
        echo "Pekerjaan: <b>$pekerjaan</b><br>";
        echo "Gaji: <b>$gaji_display</b>";
    } else {
      
        echo "<hr><h3>Hasil Data:</h3>";
        echo "Nama: <b>(Kosong)</b><br>";
        echo "Tanggal Lahir: <b>(Kosong)</b><br>";
        echo "Umur: <b>-</b><br>";
        echo "Pekerjaan: <b>-</b><br>";
        echo "Gaji: <b>-</b>";
    }
    ?>
</div>
</body>
</html>
```
# Hasilnya
<img width="2240" height="1266" alt="Cuplikan layar 2025-11-10 182746" src="https://github.com/user-attachments/assets/405849ad-8468-48e8-ab31-745f42feee1b" />

# Codingan yang suda di tambahkan css
```php
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Tugas PHP Dasar | Elegant Form</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>

        body {
            font-family: 'Poppins', sans-serif;
            background: linear-gradient(135deg, #f0f4f8 0%, #e6e9ee 100%); /* Latar belakang gradien lembut */
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
        }
        .container {
            max-width: 550px;
            width: 90%;
            background: white;
            padding: 40px;
            border-radius: 20px;
            /* Shadow yang lebih lembut dan elegan */
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08), 0 4px 12px rgba(0, 0, 0, 0.05); 
            transition: transform 0.3s ease-in-out;
        }
        .container:hover {
            transform: translateY(-2px); 
        }
        h2 {
            text-align: center;
            color: #333;
            margin-bottom: 30px;
            font-weight: 600;
            letter-spacing: 0.5px;
        }
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 400;
            color: #555;
            font-size: 14px;
        }
        input:not([type="submit"]), select {
            width: 100%;
            padding: 12px 15px;
            margin-bottom: 20px;
            border: 1px solid #ddd;
            border-radius: 10px; /* Sudut lebih membulat */
            font-size: 15px;
            color: #333;
            background-color: #f9f9f9;
            box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.05); /* Shadow input ke dalam */
            transition: all 0.3s ease;
        }
        input:focus, select:focus {
            border-color: #007bff; /* Warna fokus yang elegan */
            box-shadow: 0 0 0 3px rgba(0, 123, 255, 0.1);
            background-color: white;
            outline: none;
        }
        input[type="submit"] {
            /* Warna tombol Biru Navy/Royal Blue yang mewah */
            background: #007bff; 
            color: white;
            padding: 12px;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            letter-spacing: 0.5px;
            box-shadow: 0 4px 15px rgba(0, 123, 255, 0.3);
            transition: background 0.3s, box-shadow 0.3s;
        }
        input[type="submit"]:hover {
            background: #0056b3;
            box-shadow: 0 6px 20px rgba(0, 123, 255, 0.4);
        }
        .hasil {
            margin-top: 35px;
            background: #e9f0f7; /* Warna latar belakang hasil yang lembut */
            padding: 25px;
            border-radius: 15px;
            border-left: 5px solid #007bff; /* Garis vertikal sebagai aksen */
        }
        .hasil h3 {
            color: #007bff;
            margin-top: 0;
            border-bottom: 2px solid #007bff20;
            padding-bottom: 10px;
            font-weight: 600;
        }
        .hasil b {
            font-weight: 600;
            color: #333;
        }
    </style>
</head>
<body>
<div class="container">
    <h2>Form Biodata dan Gaji</h2>
    <form method="POST">
        <label>Nama Lengkap:</label>
        <input type="text" name="nama" required>

        <label>Tanggal Lahir:</label>
        <input type="date" name="tgl_lahir" required>

        <label>Pekerjaan:</label>
        <select name="pekerjaan" required>
            <option value="">-- Pilih Pekerjaan --</option>
            <option value="Programmer">Programmer</option>
            <option value="Desainer">Desainer</option>
            <option value="Guru">Guru</option>
            <option value="Dokter">Dokter</option>
            <option value="Mahasiswa">Mahasiswa</option>
        </select>

        <input type="submit" name="submit" value="Tampilkan">
    </form>

    <?php
    $nama = "";
    $tgl_lahir = "";
    $pekerjaan = "";
    $umur = "-";
    $gaji_display = "-";
    
    if (isset($_POST['submit'])) {
        $nama = $_POST['nama'];
        $tgl_lahir = $_POST['tgl_lahir'];
        $pekerjaan = $_POST['pekerjaan'];

        $lahir = new DateTime($tgl_lahir);
        $hari_ini = new DateTime();
        
        if ($lahir > $hari_ini) {
            $umur = 0; 
        } else {
            $selisih = $hari_ini->diff($lahir);
            $umur = $selisih->y;
        }
        
        $gaji = 0;
        switch ($pekerjaan) {
            case "Programmer":
                $gaji = 12000000;
                break;
            case "Desainer":
                $gaji = 8500000;
                break;
            case "Guru":
                $gaji = 6500000;
                break;
            case "Dokter":
                $gaji = 17000000;
                break;
            case "Mahasiswa":
                $gaji = 500000; 
                break;
            default:
                $gaji = 1000000; 
                break;
        }
        
        $gaji_display = "Rp " . number_format($gaji, 0, ',', '.');
        
       
        echo "<div class='hasil'>";
        echo "<h3>Hasil Data:</h3>";
        echo "Nama: <b>$nama</b><br>";
        echo "Tanggal Lahir: <b>" . date('d-m-Y', strtotime($tgl_lahir)) . "</b><br>";
        echo "Umur: <b>$umur tahun</b><br>";
        echo "Pekerjaan: <b>$pekerjaan</b><br>";
        echo "Gaji: <b>$gaji_display</b>";
        echo "</div>";
    } else {
      
        echo "<div class='hasil'>";
        echo "<h3>Hasil Data:</h3>";
        echo "Nama: <b>(Kosong)</b><br>";
        echo "Tanggal Lahir: <b>(Kosong)</b><br>";
        echo "Umur: <b>-</b><br>";
        echo "Pekerjaan: <b>-</b><br>";
        echo "Gaji: <b>-</b>";
        echo "</div>";
    }
    ?>
</div>
</body>
</html>
```
# Hasil jika sudah ditambahkan css
<img width="2240" height="1265" alt="Cuplikan layar 2025-11-10 182829" src="https://github.com/user-attachments/assets/cab9d4dc-a258-4275-90df-1e8f08bf407e" />





