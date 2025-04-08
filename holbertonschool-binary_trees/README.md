## C - Binary Trees

Ce fichier README fournit une vue d'ensemble sur les arbres binaires en langage C, incluant leur définition, leur représentation, leur implémentation, et les opérations courantes.

---

### **Qu'est-ce qu'un arbre binaire ?**
Un arbre binaire est une structure de données hiérarchique dans laquelle chaque nœud peut avoir au maximum deux enfants : un enfant gauche et un enfant droit. Les arbres binaires sont largement utilisés dans divers algorithmes et applications, comme les arbres de recherche binaires (BST), les tas binaires, et les arbres AVL.

---

### **Représentation des arbres binaires en C**
Un arbre binaire peut être représenté en utilisant :
1. **Liste chaînée** : Chaque nœud est défini comme une structure contenant des données et deux pointeurs vers ses enfants.
2. **Tableau** : Les nœuds sont stockés dans un tableau où les indices permettent de calculer la position des enfants.

#### Exemple de structure pour un nœud :
```c
typedef struct node {
    int data;
    struct node *leftChild;
    struct node *rightChild;
} Node;
```

---

### **Création et insertion dans un arbre binaire**
#### Création d'un nouveau nœud :
```c
Node* createNode(int value) {
    Node* newNode = (Node*)malloc(sizeof(Node));
    newNode->data = value;
    newNode->leftChild = NULL;
    newNode->rightChild = NULL;
    return newNode;
}
```

#### Insertion d'un nœud :
L'insertion dans un arbre binaire peut être réalisée de manière récursive.
```c
void insert(Node** root, int value) {
    if (*root == NULL) {
        *root = createNode(value);
    } else if (value data) {
        insert(&(*root)->leftChild, value);
    } else {
        insert(&(*root)->rightChild, value);
    }
}
```

---

### **Parcours d'un arbre binaire**
Les méthodes de parcours permettent de visiter tous les nœuds de l'arbre. Les trois principaux types sont :

1. **Parcours en pré-ordre** (racine → gauche → droite) :
```c
void preOrder(Node* root) {
    if (root != NULL) {
        printf("%d ", root->data);
        preOrder(root->leftChild);
        preOrder(root->rightChild);
    }
}
```

2. **Parcours en ordre croissant** (gauche → racine → droite) :
```c
void inOrder(Node* root) {
    if (root != NULL) {
        inOrder(root->leftChild);
        printf("%d ", root->data);
        inOrder(root->rightChild);
    }
}
```

3. **Parcours en post-ordre** (gauche → droite → racine) :
```c
void postOrder(Node* root) {
    if (root != NULL) {
        postOrder(root->leftChild);
        postOrder(root->rightChild);
        printf("%d ", root->data);
    }
}
```

---

### **Opérations courantes**
1. **Recherche** : Trouver un élément dans l'arbre.
   ```c
   Node* search(Node* root, int value) {
       if (root == NULL || root->data == value)
           return root;
       if (value data)
           return search(root->leftChild, value);
       return search(root->rightChild, value);
   }
   ```

2. **Calcul de la hauteur** : Mesurer la profondeur de l'arbre.
   ```c
   int height(Node* root) {
       if (root == NULL)
           return 0;
       int leftHeight = height(root->leftChild);
       int rightHeight = height(root->rightChild);
       return 1 + ((leftHeight > rightHeight) ? leftHeight : rightHeight);
   }
   ```

3. **Comptage des feuilles** : Nombre de nœuds sans enfants.
   ```c
   int countLeaves(Node* root) {
       if (root == NULL)
           return 0;
       if (root->leftChild == NULL && root->rightChild == NULL)
           return 1;
       return countLeaves(root->leftChild) + countLeaves(root->rightChild);
   }
   ```

---

### **Exemple d'utilisation**
Voici un exemple simple montrant comment créer un arbre binaire, y insérer des valeurs et effectuer différents parcours :
```c
int main() {
    Node* root = NULL;

    insert(&root, 10);
    insert(&root, 5);
    insert(&root, 15);

    printf("Parcours en ordre croissant : ");
    inOrder(root);

    printf("\nHauteur de l'arbre : %d\n", height(root));

    return 0;
}
```

---

### **Conclusion**
Les arbres binaires sont une structure fondamentale en informatique. Leur implémentation en C offre une flexibilité grâce à l'utilisation des pointeurs pour gérer dynamiquement les nœuds et leurs relations.

Citations:
[1] https://www.scaler.com/topics/binary-tree-in-c/
[2] https://dev.to/shafspecs/exploring-binary-trees-in-c-jlk
[3] https://gist.github.com/fcannizzaro/904669021365b71f296a
[4] https://takeuforward.org/binary-tree/binary-tree-representation-in-c/
[5] https://github.com/allelomorph/binary_trees
[6] https://www.tutorialspoint.com/dsa_using_c/dsa_using_c_tree.htm
[7] https://www.wscubetech.com/resources/dsa/binary-tree
[8] https://www.reddit.com/r/C_Programming/comments/frbbzq/binary_tree_implementation/
[9] https://www.cprogramming.com/tutorial/c/lesson18.html
[10] https://gist.github.com/tsprates/8cefd5c7f855120c83c9462ddb99b845
[11] https://www.learn-c.org/en/Binary_trees
[12] http://cslibrary.stanford.edu/110/BinaryTrees.html
[13] https://scaler.com/topics/images/trees-in-c.webp?sa=X&ved=2ahUKEwiw9rL19seMAxVygv0HHeW9LWAQ_B16BAgDEAI
[14] https://www.youtube.com/watch?v=hfwwaNNJ-0A
[15] https://study.com/academy/lesson/binary-trees-applications-implementation.html
[16] https://www.w3schools.com/dsa/dsa_data_binarytrees.php
[17] https://www.youtube.com/watch?v=4s1Tcvm00pA
[18] https://www.youtube.com/watch?v=ktM-rDzquyU
[19] https://www.youtube.com/watch?v=UbhlOk7vjVY
[20] https://www.programiz.com/dsa/binary-tree

---