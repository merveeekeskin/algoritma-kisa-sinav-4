# algoritma-kisa-sinav-4
#include <stdio.h>


#include <stdlib.h>



// Düğüm yapısını tanımlıyoruz


struct dugum {


    int veri; // Düğümün verisini tutacak değişken
    
    
    struct dugum *sonraki; // Düğümün sonraki düğümüne işaret edecek pointer
    
    
};


// İlk ve son düğümleri tutacak pointerlarımızı NULL olarak tanımlıyoruz


struct dugum *ilk = NULL;


struct dugum *son = NULL;



// Ekleme işlemini gerçekleştiren fonksiyon


void ekle(int veri) {


    // Yeni bir düğüm oluşturuyoruz ve verisini atıyoruz
    
    
    struct dugum *yeniDugum = (struct dugum*)malloc(sizeof(struct dugum));
    
    
    yeniDugum->veri = veri;
    
    
    yeniDugum->sonraki = NULL;
    
    
    // Eğer kuyruk boşsa ilk ve son düğümlerimizi yeni düğüm olarak atıyoruz
    
    
    if(ilk == NULL && son == NULL) {
    
    
        ilk = son = yeniDugum;
        
        
        return;
        
        
    }
    
    
    // Kuyruk boş değilse son düğümün sonrakisi olarak yeni düğümü ekliyoruz ve son düğümü güncelliyoruz
    
    
    son->sonraki = yeniDugum;
    
    
    son = yeniDugum;
    
    
}


// Silme işlemini gerçekleştiren fonksiyon


void sil() {


    struct dugum *gecici = ilk;
    
    
    // Eğer kuyruk boşsa uyarı veriyoruz
    
    
    if(ilk == NULL) {
    
    
        printf("Kuyruk bos\n");
        
        
        return;
        
        
    }
    
    
    // Eğer kuyrukta sadece bir eleman varsa ilk ve son düğümlerimizi NULL yapıyoruz
    
    
    if(ilk == son) {
    
    
        ilk = son = NULL;
        
        
    }
    
    
    // Kuyrukta birden fazla eleman varsa ilk düğümümüzü güncelliyoruz
    
    
    else {
    
    
        ilk = ilk->sonraki;
        
        
    }
    
    
    // İlk düğümü siliyoruz
    
    
    free(gecici);
    
    
}


// Görüntüleme işlemini gerçekleştiren fonksiyon


void goruntule() {


    struct dugum *gecici = ilk;
    
    
    // Eğer kuyruk boşsa uyarı veriyoruz
    
    
    if(ilk == NULL) {
    
    
        printf("Kuyruk bos\n");
        
        
        return;
        
    }
    
    
    // Kuyruktaki tüm elemanları görüntülüyoruz
    
    
    while(gecici != NULL) {
    
    
        printf("%d ", gecici->veri);
        
        
        gecici = gecici->sonraki;
        
        
    }
    
    
    printf("\n");
    
    
}


int main() {


    int secim, veri;
    
    
    while(1) {
    
    
        printf("Lutfen asagidaki islemlerden birini seciniz:\n");
        
        
        printf("1. Ekleme\n2. Silme\n3. Goruntuleme\n4. Cikis\n");
        
        
        scanf("%d", &secim);
        
        
        switch(secim) {
        
        
            case 1: printf("Eklemek istediginiz sayiyi giriniz: ");
            
            
                    scanf("%d", &veri);
                    
                    
                    ekle(veri);
                    
                    
                    break;
                    
                    
            case 2: sil();
            
            
                    break;
                    
                    
            case 3: goruntule();
            
            
                    break;
                    
                    
            case 4: exit(0);
            
            
            default: printf("Gecersiz secim!\n");
            
            
        }
        
        
    }
    
    
}
