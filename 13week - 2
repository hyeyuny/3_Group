'''
#define _CRT_SECURE_NO_WARNINGS
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

struct Book {
    char Title[50];
    char Authors[50];
    char Press[50];
    int Page;
    int Price;
    char borrow[20];
};

void BookList(struct Book* library, int size);
void searchBook(struct Book* library, int size);
void borrowBook(struct Book* library, int size);
void returnBook(struct Book* library, int size);
char tolower(char c);

int main() {
    int choice;
    const int MAX_BOOKS = 5;

    struct Book* library = (struct Book*)malloc(MAX_BOOKS * sizeof(struct Book));

    if (library == NULL) {
        printf("메모리 할당 실패.\n");
        return 1;
    }

    strcpy(library[0].Title, "Truth");
    strcpy(library[0].Authors, "John");
    strcpy(library[0].Press, "Century");
    library[0].Page = 300;
    library[0].Price = 20000;
    strcpy(library[0].borrow, "available");

    strcpy(library[1].Title, "Love");
    strcpy(library[1].Authors, "Paul");
    strcpy(library[1].Press, "Goods");
    library[1].Page = 200;
    library[1].Price = 15000;
    strcpy(library[1].borrow, "available");

    strcpy(library[2].Title, "Joy");
    strcpy(library[2].Authors, "James");
    strcpy(library[2].Press, "Cookie");
    library[2].Page = 250;
    library[2].Price = 18000;
    strcpy(library[2].borrow, "available");

    strcpy(library[3].Title, "Thanks");
    strcpy(library[3].Authors, "Mark");
    strcpy(library[3].Press, "Saejong");
    library[3].Page = 240;
    library[3].Price = 21000;
    strcpy(library[3].borrow, "available");

    strcpy(library[4].Title, "God");
    strcpy(library[4].Authors, "Johnson");
    strcpy(library[4].Press, "Jungjo");
    library[4].Page = 450;
    library[4].Price = 35000;
    strcpy(library[4].borrow, "available");

    do {
        printf("[도서목록] [검색] [대출] [반납] [종료]\n");
        printf("원하는 기능을 선택하세요: ");
        scanf("%d", &choice);
        printf("\n");

        switch (choice) {
        case 1:
            BookList(library, MAX_BOOKS);
            break;
        case 2:
            searchBook(library, MAX_BOOKS);
            break;
        case 3:
            borrowBook(library, MAX_BOOKS);
            break;
        case 4:
            returnBook(library, MAX_BOOKS);
            break;
        case 5:
            printf("프로그램을 종료합니다.\n");
            break;
        default:
            printf("올바른 선택이 아닙니다. 다시 선택하세요.\n");
        }

    } while (choice != 5);

    free(library);

    return 0;
}

void BookList(struct Book* library, int size) {
    printf("Title\tAuthors\tPress\tPage\tPrice\tBorrow\n");
    printf("--------------------------------------------------\n");
    for (int i = 0; i < size; ++i) {
        printf("%s\t%s\t%s\t%d\t%d\t%s\n", library[i].Title, library[i].Authors, library[i].Press, library[i].Page, library[i].Price, library[i].borrow);
    }
    printf("--------------------------------------------------\n");
    printf("\n");
}

void searchBook(struct Book* library, int size) {
    char searchTitle[50];
    printf("검색할 도서를 입력하세요: ");
    scanf("%s", searchTitle);
    printf("\n");

    for (int i = 0; i < size; ++i) {
        int j;
        for (j = 0; searchTitle[j] && tolower(searchTitle[j]) == tolower(library[i].Title[j]); ++j);
        if (!searchTitle[j]) {
            printf("Title\tAuthors\tPress\tPage\tPrice\tBorrow\n");
            printf("--------------------------------------------------\n");
            printf("%s\t%s\t%s\t%d\t%d\t%s\n", library[i].Title, library[i].Authors, library[i].Press, library[i].Page, library[i].Price, library[i].borrow);
            printf("--------------------------------------------------\n");
            printf("\n");
            return;
        }
    }

    printf("해당 도서를 찾을 수 없습니다.\n");
    printf("\n");
}

void borrowBook(struct Book* library, int size) {
    char borrowTitle[50];
    printf("대출할 도서를 입력하세요: ");
    scanf("%s", borrowTitle);
    printf("\n");

    for (int i = 0; i < size; ++i) {
        int j;
        for (j = 0; borrowTitle[j] && tolower(borrowTitle[j]) == tolower(library[i].Title[j]); ++j);
        if (!borrowTitle[j]) {
            if (strcmp(library[i].borrow, "available") == 0) {
                strcpy(library[i].borrow, "borrowing");
                printf("대출 되었습니다.\n");
                printf("\n");
            }
            else {
                printf("대출 중이라 대출 할 수 없습니다.\n");
                printf("\n");
            }
            return;
        }
    }

    printf("해당 도서를 찾을 수 없습니다.\n");
    printf("\n");
}

void returnBook(struct Book* library, int size) {
    char returnTitle[50];
    printf("반납할 도서를 입력하세요: ");
    scanf("%s", returnTitle);
    printf("\n");

    for (int i = 0; i < size; ++i) {
        int j;
        for (j = 0; returnTitle[j] && tolower(returnTitle[j]) == tolower(library[i].Title[j]); ++j);
        if (!returnTitle[j]) {
            if (strcmp(library[i].borrow, "borrowing") == 0) {
                strcpy(library[i].borrow, "available");
                printf("책이 반납 되었습니다.\n");
                printf("\n");
            }
            else {
                printf("대출 되지 않은 책입니다.\n");
                printf("\n");
            }
            return;
        }
    }

    printf("해당 도서를 찾을 수 없습니다.\n");
    printf("\n");
}

char tolower(char c) {
    if (c >= 'A' && c <= 'Z') {
        return c + ('a' - 'A');
    }
    return c;
}
'''
