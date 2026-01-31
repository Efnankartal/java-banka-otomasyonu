# java-banka-otomasyonu
bu proje Java programlama dilini kullanılarak geliştirilmiş basit bir konsol tabanlı banka otomasyonudur. 

package nesneT;
import java.util.Scanner;
public class BankaHesabi {
	private String hesapSahibi;
    private double bakiye;

    public BankaHesabi(String hesapSahibi, double baslangicBakiye) {
        this.hesapSahibi = hesapSahibi;
        this.bakiye = baslangicBakiye;
    }

    public void paraYatir(double miktar) {
        if (miktar > 0) {
            bakiye += miktar;
            System.out.println("Para yatırıldı. Yeni bakiye: " + bakiye + " TL");
        } else {
            System.out.println("Geçersiz miktar!");
        }
    }

    public void paraCek(double miktar) {
        if (miktar > 0 && miktar <= bakiye) {
            bakiye -= miktar;
            System.out.println("Para çekildi. Yeni bakiye: " + bakiye + " TL");
        } else {
            System.out.println("Yetersiz bakiye veya geçersiz miktar!");
        }
    }

    public void bakiyeGoster() {
        System.out.println("Hesap sahibi: " + hesapSahibi);
        System.out.println("Mevcut bakiye: " + bakiye + " TL");
    }
}

public class Bankauygulamasi {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Hesap sahibinin adını girin: ");
        String ad = scanner.nextLine();

        System.out.print("Başlangıç bakiyesi girin: ");
        double baslangicBakiye = scanner.nextDouble();

        BankaHesabi hesap = new BankaHesabi(ad, baslangicBakiye);

        int secim;

        do {
            System.out.println("\n--- BANKA OTOMASYONU ---");
            System.out.println("1 - Bakiye Görüntüle");
            System.out.println("2 - Para Yatır");
            System.out.println("3 - Para Çek");
            System.out.println("0 - Çıkış");
            System.out.print("Seçiminiz: ");
            secim = scanner.nextInt();

            switch (secim) {
                case 1:
                    hesap.bakiyeGoster();
                    break;
                case 2:
                    System.out.print("Yatırılacak miktar: ");
                    double yatir = scanner.nextDouble();
                    hesap.paraYatir(yatir);
                    break;
                case 3:
                    System.out.print("Çekilecek miktar: ");
                    double cek = scanner.nextDouble();
                    hesap.paraCek(cek);
                    break;
                case 0:
                    System.out.println("Çıkış yapılıyor...");
                    break;
                default:
                    System.out.println("Geçersiz seçim!");
            }
        } while (secim != 0);

    }

}
