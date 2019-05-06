# nyicil-tugas-besar
tugas besar nyicil

#include<iostream>
#include<cstdlib>
#include<conio.h>
using namespace std;

struct TNode{
    int data;
    TNode *next;
};TNode *head, *tail,*depan,*belakang;

void init(){
    head=NULL;
    tail=NULL;
    depan=NULL;
    belakang=NULL;
}

int isEmpty(){
    if(tail==NULL){
    return 1;
    }else{
        return 0;
    }
}
void insertDepan(int databaru)
{
    TNode *baru;
    baru =new TNode;
    baru->data=databaru;
    baru->next=NULL;
    if(isEmpty()==1)
    {
        head=tail=baru;
        tail->next=NULL;
    }else{
        baru->next=head;
        head=baru;
    }
    cout<<"Input berhasil";
}

void insertBelakang(int data){
    TNode *baru;
    baru=new TNode;
    baru->data=data;
    baru->next=NULL;
    if(isEmpty()==1){
        head=baru;
        tail=baru;
        tail->next=NULL;
    }else
    {
        tail->next=baru;
        tail=baru;
    }
    cout<<"\n Input berhasil"<<endl;
}
void hapusDepan(){
    TNode *hapus;
    int d;
    if(isEmpty()==0){
        if(depan!=belakang){
            hapus=depan;
            d=hapus->data;
            depan=depan->next;
            delete hapus;
        }else{
            d=belakang->data;
            depan=belakang=NULL;
        }
        cout<<d<<"Terhapus";
    }else cout<<"Masih kosong\n";
}
void hapusBelakang(){
    TNode *bantu,*hapus;
    int d;
    if(isEmpty()==0){
        bantu=depan;
        if(depan!=belakang){
            while(bantu->next!=belakang){
                bantu=bantu->next;
            }
            hapus=belakang;
            belakang=bantu;
            d=hapus->data;
            delete hapus;
            belakang->next=NULL;
        }else{
            d=belakang->data;
            depan=belakang=NULL;
        }
        cout<<d<<"Terhapus\n";
    }else cout<<"Masih kosong\n";
}
void tampil(){
    TNode *bantu;
    bantu=head;
    if(isEmpty()==0){
        cout<<"depan :";
         while(bantu!=NULL){
            cout<<bantu->data<<"->";
            bantu=bantu->next;
        }
    }else if(isEmpty()==0){
        cout<<"belakang :";
        while(bantu!=NULL){
            cout<<bantu->data<<"->";
            bantu=bantu->next;
        }
     cout<<"\n Data masih kosong"<<endl;
    }
}
main(){
    int pil,data,databaru;
    init();
    do{
        system("cls");
        cout<<endl;
        cout<<"Rumah sakit"<<endl;
        cout<<"-------------------------"<<endl;
        cout<<"1. Data pasien"<<endl;
        cout<<"2. Data poli"<<endl;
        cout<<"3. Transaksi Pendaftaran"<<endl;
        cout<<"0. keluar"<<endl;
        cout<<"-------------------------"<<endl;
        cout<<"masukkan pilihan :";cin>>pil;
        switch(pil){
            case 1: system("cls");{
                cout<<"\nData pasien"<<endl;
                cout<<"-------------"<<endl;
                cout<<"masukan data dan isi data tersebut :"<<endl;
                cout<<"Nama"<<endl;
                cout<<"Alamat"<<endl;
                cout<<"Tempat tanggal lahir"<<endl;
                cout<<"Jenis kelamin"<<endl;
				cout<<"nomer antrian"<<endl;
                cout<<"masukkan data : ";cin>>databaru;
                insertDepan(databaru);
                break;
            }
            case 2: system("cls");{
                cout<<"\nData poli"<<endl;
                cout<<"-------------"<<endl;
                cout<<"masukkan data : ";cin>>data;
                insertBelakang(data);
                break;
            }
            case 3: system("cls");{
                cout<<"\nTransaksi pendaftaran"<<endl;
                hapusDepan();
                break;
            }
            case 0 : system("cls");{
                return 0;
                break;
            }default:
            system ("cls");{
                cout<<"pilihan tidak tersedia"<<endl;
            }
        }getch();
    }while(pil!=7);
}
