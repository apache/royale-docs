import flash.events.MouseEvent;
import flash.events.Event;

stop();

// Daftar 5 benda hasil Spinwheel sesuai draf
var daftarBenda:Array = ["Laptop (Desain Grafis)", "HT (Petugas Keamanan)", "Hair dryer (Salon)", "Diesel Air (Petani)", "Kunci Pas Soket (Teknisi Otomotif)"]; [cite: 9]

// Fungsi memutar roda
tombolPutar_btn.addEventListener(MouseEvent.CLICK, putarRoda);

function putarRoda(event:MouseEvent):void {
    tombolPutar_btn.enabled = false; // Matikan tombol saat berputar
    teksTugas_txt.text = "Memilih benda...";
    
    // Menentukan rotasi acak (minimal 3 putaran penuh + sudut acak)
    var rotasiTujuan:Number = (Math.random() * 360) + 1080;
    
    // Jalankan animasi putar sederhana
    addEventListener(Event.ENTER_FRAME, function(e:Event):void {
        roda_mc.rotation += 25; // Kecepatan putar
        
        if (roda_mc.rotation >= rotasiTujuan) {
            removeEventListener(Event.ENTER_FRAME, arguments.callee);
            tombolPutar_btn.enabled = true;
            tentukanBenda(roda_mc.rotation % 360);
        }
    });
}

// Fungsi menentukan benda apa yang didapat berdasarkan sudut berhenti
function tentukanBenda(sudut:Number):void {
    var indeksBenda:int = Math.floor(sudut / (360 / daftarBenda.length));
    var bendaTerpilih:String = daftarBenda[indeksBenda];
    
    // Tampilkan instruksi untuk anak tunarungu di layar
    teksTugas_txt.text = "Kamu mendapatkan: " + bendaTerpilih + "!\nBuatlah kalimat S-P-O-K sesuai benda ini."; [cite: 8]
}
