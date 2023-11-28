# 자바 당근마켓 웹크롤링 프로젝트

```java
import org.jsoup.Connection;
import org.jsoup.Jsoup;
import org.jsoup.nodes.Document;
import org.jsoup.nodes.Element;
import org.jsoup.select.Elements;

import java.io.IOException;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int num, check, nav;
        System.out.println("인기매물 불러오기 : 1 | 알바 불러오기 : 2 | 당근 채팅 시작하기 : 3 | 당근마켓 인스타그램 : 4");
        nav = scanner.nextInt();
        if (nav == 1) {
            System.out.println("불러올 게시물 수를 입력해주세요.");
            num = scanner.nextInt();
            final String Url = "https://www.daangn.com/hot_articles";
            Connection conn = Jsoup.connect(Url);
            System.out.println("당근마켓 인기매물 불러오기");
            try {
                Document document = conn.get();
                Elements titleElements = document.select("a > div.card-desc > h2 ");
                Elements priceElements = document.select("a > div.card-desc > div.card-price ");
                Elements regionElements = document.select("a > div.card-desc > div.card-region-name");
                Elements contsElements = document.select("a > div.card-desc > div.card-counts");

                for (int k = 0; k < num; k++) {
                    final String title = titleElements.get(k).text();
                    final String price = priceElements.get(k).text();
                    final String region = regionElements.get(k).text();
                    final String counts = contsElements.get(k).text();

                    System.out.println(k + "번 게시물");
                    System.out.println("당근 마켓 게시물 제목 : " + title);
                    System.out.println("가격 : " + price);
                    System.out.println("위치 : " + region);
                    System.out.println(counts);
                    System.out.println("===================================================");
                }

                System.out.println("당근마켓 주소 보기 : 1 | 주소 안보기 : 0");
                check = scanner.nextInt();
                if (check == 1) {
                    System.out.println(Url);
                } else {
                    System.out.println("종료");
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        } else if(nav == 2) {
            System.out.println("불러올 게시물 수를 입력해주세요.");
            num = scanner.nextInt();
            final String Url = "https://www.daangn.com/kr/jobs/";
            Connection conn = Jsoup.connect(Url);
            System.out.println("당근마켓 알바 게시물 불러오기");

            try {
                Document document = conn.get();
                Elements titleElements = document.select("a > article.w7pzr90.w7pzr92 > div.w7pzr97.w7pzr99 > div.w7pzr93");
                Elements regionElements = document.select("a > article.w7pzr90.w7pzr92 > div.w7pzr97.w7pzr99 > div.w7pzr94");
                Elements priceElements = document.select("a > article.w7pzr90.w7pzr92 > div.w7pzr97.w7pzr99 > div.w7pzr95");
                for (int k = 0; k < num; k++) {
                    final String title = titleElements.get(k).text();
                    final String region = regionElements.get(k).text();
                    final String price = priceElements.get(k).text();

                    System.out.println(k + "번 게시물");
                    System.out.println("당근 마켓 게시물 제목 : " + title);
                    System.out.println("위치 : " + region);
                    System.out.println("가격 : " + price);
                    System.out.println("===================================================");
                }

                System.out.println("당근마켓 주소 보기 : 1 | 주소 안보기 : 0");
                check = scanner.nextInt();
                if (check == 1) {
                    System.out.println(Url);
                } else {
                    System.out.println("종료");
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        } else if(nav == 3){
            final String Url = "https://chat.daangn.com/login";
            System.out.println("채팅 시작하기 : " + Url);
        } else if(nav == 4) {
            final String Url = "https://www.instagram.com/daangnmarket/?_fp=25f56e7425d61deadec81e36ebb949aa";
            System.out.println("인스타그램 : " + Url);
        } else {
            System.out.println("입력 방식이 잘못되었습니다.");
        }
    }
}
```
