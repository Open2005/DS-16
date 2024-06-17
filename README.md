Write a C program to create a hash table and perform collision resolution using the following techniques. (i) Open addressing (ii) Closed Addressing (iii) Rehashing

Algorithm: CODE: i)Open Addressing: #include <stdio.h> #include <stdlib.h> #include <stdbool.h>

#define SIZE 10

struct HashNode { int key; int value; bool occupied; };

struct HashNode* createHashNode(int key, int value) { struct HashNode* newNode = (struct HashNode*)malloc(sizeof(struct HashNode)); newNode->key = key; newNode->value = value; newNode->occupied = true; return newNode; }

struct HashNode** createHashTable() { struct HashNode** table = (struct HashNode**)malloc(SIZE * sizeof(struct HashNode*)); for (int i = 0; i < SIZE; i++) { table[i] = NULL; } return table; }

int hashCode(int key) { return key % SIZE; }

void insertOpenAddressing(struct HashNode** table, int key, int value) { int index = hashCode(key); while (table[index] != NULL && table[index]->occupied) { index = (index + 1) % SIZE; } table[index] = createHashNode(key, value); }

void displayHashTable(struct HashNode** table) { printf("Hash Table:\n"); for (int i = 0; i < SIZE; i++) { if (table[i] != NULL && table[i]->occupied) { printf("Index %d: Key = %d, Value = %d\n", i, table[i]->key, table[i]->value); } else { printf("Index %d: Empty\n", i); } } }

int main() { struct HashNode** hashTable = createHashTable();

insertOpenAddressing(hashTable, 5, 10);
insertOpenAddressing(hashTable, 15, 20);
insertOpenAddressing(hashTable, 25, 30);
insertOpenAddressing(hashTable, 35, 40);
insertOpenAddressing(hashTable, 45, 50);
insertOpenAddressing(hashTable, 55, 60);
insertOpenAddressing(hashTable, 65, 70);
insertOpenAddressing(hashTable, 75, 80);
insertOpenAddressing(hashTable, 85, 90);
insertOpenAddressing(hashTable, 95, 100);

displayHashTable(hashTable);

return 0;
}
