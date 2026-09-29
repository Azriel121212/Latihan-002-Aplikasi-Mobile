# Latihan Dart - Sistem Diskon

Latihan pertemuan ke 2 menggunakan **Dart** untuk menghitung total pembayaran berdasarkan jumlah belanja dan status member.

## Deskripsi

Program menerapkan beberapa aturan diskon:

* Belanja minimal Rp100.000 mendapatkan diskon 10%.
* Member mendapatkan tambahan diskon 5%.
* Potongan diskon maksimal Rp25.000.

## Kelompok

Deny Dermawan & Chairul Azriel


````dart

void main() {
  // Case 1
  int belanja1 = 80000;
  bool member1 = false;

  print("Skenario 1");  // Menampilkan judul skenario
  print("Total Belanja: Rp$belanja1"); // Menampilkan total belanja
  print("Member: $member1"); // Menampilkan status pelanggan, apakah member atau bukan
  print("Total Bayar: Rp${hitungTotalBayar(belanja1, member1)}"); // Menghitung dan menampilkan total yang harus dibayar setelah diskon

  print(""); // Spasi kosong untuk memisahkan output (Biar rapih)

  // Case 2
  int belanja2 = 150000;
  bool member2 = false;

  print("Skenario 2");
  print("Total Belanja: Rp$belanja2");
  print("Member: $member2");
  print("Total Bayar: Rp${hitungTotalBayar(belanja2, member2)}");

  print("");

  // Case 3
  int belanja3 = 150000;
  bool member3 = true;

  print("Skenario 3");
  print("Total Belanja: Rp$belanja3");
  print("Member: $member3");
  print("Total Bayar: Rp${hitungTotalBayar(belanja3, member3)}");

  print("");

  // Case 4
  int belanja4 = 300000;
  bool member4 = true;

  print("Skenario 4");
  print("Total Belanja: Rp$belanja4");
  print("Member: $member4");
  print("Total Bayar: Rp${hitungTotalBayar(belanja4, member4)}");
}


// Fungsi untuk menentukan persentase diskon
int hitungPersenDiskon(int totalBelanja, bool member) {
  int persenDiskon = 0;

  // BR-01
  // Jika total belanja >= 100.000, berikan diskon 10%
  if (totalBelanja >= 100000) {
    persenDiskon = 10;

    // BR-02
    // Jika pelanggan adalah member, tambahkan diskon 5%
    if (member) {
      persenDiskon += 5;
    }
  }

  // Jika total belanja < 100.000, tidak ada diskon
  else {
    persenDiskon = 0;
  }

  return persenDiskon;
}


// Fungsi untuk menghitung nominal potongan
int hitungPotongan(int totalBelanja, int persenDiskon) {
  int potongan = totalBelanja * persenDiskon ~/ 100;

  // BR-03
  // Jika potongan > 25.000, batasi maksimal 25.000
  if (potongan > 25000) {
    potongan = 25000;
  }

  return potongan;
}


// Fungsi untuk menghitung total bayar
int hitungTotalBayar(int totalBelanja, bool member) {
  // Hitung persentase diskon
  int persenDiskon = hitungPersenDiskon(totalBelanja, member);

  // Hitung nominal potongan
  int potongan = hitungPotongan(totalBelanja, persenDiskon);

  return totalBelanja - potongan;
}

````
