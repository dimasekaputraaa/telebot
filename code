var token = "token";
var SheetID = "sheetID";
var telegramUrl = "https://api.telegram.org/bot" + token;
var webAppUrl = "WEBAPP";

function doPost(e) {
var stringJson = e.postData.getDataAsString();
var updates = JSON.parse(stringJson);
var msg = updates.message.text;
var inputan = msg.split(" ");
//sendData('719598768', stringJson);
  if(msg=='/start'){
    sendData(updates.message.chat.id,"silahkan pilih menu ", keyb); 
  }
  else if(msg=='cara menggunakan'){
    sendData(updates.message.chat.id,
             'Silahkan Masukan kata kunci'); 
  }
  else if(msg=='kata kunci'){
    sendData(updates.message.chat.id,
             'Berikut adalah kata kuncinya : \ncek summary lunas --> "sum lunas KODE" \ncek summary belum lunas --> "sum belum lunas KODE" \ncek saldo lunas --> "saldo lunas KODE"\ncek saldo belum lunas --> "saldo belum lunas KODE"'); 
  }
  else if(inputan[0]=="sum" && inputan[1]=="lunas"){
    sendData(updates.message.chat.id,sumLunas(inputan[2])); 
  }
    else if(inputan[0]=="sum" && inputan[1]=="belum" && inputan[2]=="lunas"){
    sendData(updates.message.chat.id,sumBelum(inputan[3])); 
  }
  else if(inputan[0]=="saldo" && inputan[1]=="lunas"){
    sendData(updates.message.chat.id, CDL(inputan[2])); 
  }
  else if(inputan[0]=="saldo" && inputan[1]=="belum"){
    sendData(updates.message.chat.id, CbbDL(inputan[3])); 
  }
  else {
  sendData(updates.message.chat.id, "silahkan tulis /start");
  }

}

function setWebhook() {
  var url = telegramUrl + "/setWebhook?url=" + webAppUrl;
  var response = UrlFetchApp.fetch(url);
  Logger.log(response.getContentText());
}

    
function cek(){
  var rangeName = 'NAME!A2:BH';
  var value = Sheets.Spreadsheets.Values.get(SheetID, rangeName).values;
  return value;
}


function sumLunas(id){
  var cekData = cek();
  var res;
  var data = [];
  for (var row = 0; row < cekData.length; row++) {
    if(cekData[row][53]==id && cekData[row][44]=="LUNAS"){
        res = "Kcontact : " + cekData[row][51] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57];
        data.push("\n\n======================\n"+res);
    }
    else if(cekData[row][59]==id && cekData[row][44]=="LUNAS"){
        res = "Kode SPV : " + cekData[row][59] +
              "\nSupervisor : " + cekData[row][57] +
              "\nAgency : " + cekData[row][55];
        data.push("\n\n======================\n"+res);
    }
    else if(cekData[row][46]==id && cekData[row][44]=="LUNAS"){
        res = "STO : " + cekData[row][46];
        data.push("\n\n======================\n"+res);
    }
    else if(cekData[row][58]==id && cekData[row][44]=="LUNAS"){
        res = "Kode SPN : " + cekData[row][58];
        data.push("\n\n======================\n"+res);
    }
  }
  if(data.length==0){
    return "Data Tidak ditemukan";
  }
  return ""+res+"\nsaldo yang tersedia : "+data.length;
}

function sumBelum(id){
  var cekData = cek();
  var res;
  var data = [];
  for (var row = 0; row < cekData.length; row++) {
    if(cekData[row][53]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "Kcontact : " + cekData[row][53] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57];
        data.push("\n\n======================\n"+res);
    }
    else if(cekData[row][59]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "Kode SPV : " + cekData[row][59] +
              "\nSupervisor : " + cekData[row][57] +
              "\nAgency : " + cekData[row][55];
        data.push("\n\n======================\n"+res);
    }
    else if(cekData[row][46]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "STO : " + cekData[row][46];
        data.push("\n\n======================\n"+res);
    }
    else if(cekData[row][58]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "Kode Agency : " + cekData[row][58];
        data.push("\n\n======================\n"+res);
    }
  }
  if(data.length==0){
    return "Data Tidak ditemukan";
  } 
  return ""+res+"\nsaldo yang tersedia : "+data.length;
}


function CDL(id){
  var cekData = cek();
  var res;
  var resi;

  var data = [];
  var datas = data.sort();


  for (var row = 0; row < cekData.length; row++) {
      if(cekData[row][53]==id && cekData[row][44]=="LUNAS"){
        res = "Kcontact : " + cekData[row][53] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
              "\nSTO : " + cekData[row][46] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
                "\nStatus Pembayaran : Lunas";
        data.push("\n\n======================\n"+res);
      }
    else if(cekData[row][59]==id && cekData[row][44]=="LUNAS"){
        res = "Kode SPV : " + cekData[row][59] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
              "\nSTO : " + cekData[row][46] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
                "\nStatus Pembayaran : Lunas";
        data.push("\n\n======================\n"+res);
      }
    else if(cekData[row][46]==id && cekData[row][44]=="LUNAS"){
        res = "STO : " + cekData[row][46] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
                "\nStatus Pembayaran : Lunas";
        data.push("\n\n======================\n"+res);
      }
    else if(cekData[row][58]==id && cekData[row][44]=="LUNAS"){
        res = "Kode Agency : " + cekData[row][58] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
              "\nSTO : " + cekData[row][46] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
              "\nStatus Pembayaran : Belum Lunas";
        data.push(" \n\n======================\n"+res);
    }
  }
  if(data.length==0){
    return "Data Tidak ditemukan";
  } 
 
    return "Saldo yang tersedia "+datas.splice(0,5);
}

                                             
                                             

function CbbDL(id){
  var cekData = cek();
  var res;
  var data = [];
  var datas = data.sort();
  for (var row = 0; row < cekData.length; row++) { 
    if(cekData[row][53]==id && cekData[row][44]=="BELUM LUNAS"){
      res = "Kcontact : " + cekData[row][53] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
              "\nSTO : " + cekData[row][46] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
              "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
                "\nStatus Pembayaran : Belum Lunas";
        data.push("\n\n======================\n"+res);
      }
    else if(cekData[row][59]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "Kode SPV : " + cekData[row][59] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
              "\nSTO : " + cekData[row][46] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
                "\nStatus Pembayaran : Belum Lunas";
        data.push("\n\n======================\n"+res);
      }
    else if(cekData[row][46]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "STO : " + cekData[row][46] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
                "\nStatus Pembayaran : Belum Lunas";
        data.push("\n\n======================\n"+res);
      }
    else if(cekData[row][58]==id && cekData[row][44]=="BELUM LUNAS"){
        res = "Kode Agency : " + cekData[row][58] +
              "\nNama Agent : " + cekData[row][54] +
              "\nAgency : " + cekData[row][55] +
              "\nSupervisor : " + cekData[row][57] +
              "\nSTO : " + cekData[row][46] +
               "\n======================"+
               "\nInternet : " + cekData[row][3] +
               "\nNama Pelanggan : " + cekData[row][8] +
              "\nAlamat : " + cekData[row][9] +
              "\nCP 1 : " + cekData[row][47] +
              "\nCP 2 : " + cekData[row][48] +
              "\nEmail : " + cekData[row][50] +
              "\nJumlah Tagihan : Rp." + cekData[row][31] +
              "\nStatus Pembayaran : Belum Lunas";
        data.push(" \n\n======================\n"+res);
    }
  }
  if(data.length==0){
    return "Data Tidak ditemukan";
  } 
 
    return "Saldo yang tersedia "+datas.slice(0, 5,);
}                                             
                                             

function tesCek(){
  var nama = saldo(SPAH96H);
  var x = "";
 
}
var keyb = {
  "keyboard":[
    [{"text": "cara menggunakan"}, {"text": "kata kunci"}]
  ]
}

function sendData(chatid,text,replymarkup){
var data = {
    method: "post",
    payload: {
      method: "sendMessage",
      chat_id: String(chatid),
      text: text,
      parse_mode: "HTML",
      reply_markup: JSON.stringify(replymarkup)
    }
  };
  UrlFetchApp.fetch('https://api.telegram.org/bot' + token + '/', data);
}
