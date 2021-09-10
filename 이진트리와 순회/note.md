```
package algo;


/**
 * 이진 트리와 순회
 *
 * 1. 전위 순회 preorder
 * - 먼저 자기 자신을 처리
 * - 왼쪽 자식 방문
 * - 오른쪽 자식 방문
 *
 * 2. 중위 순회 inorder
 * - 왼쪽 자식을 방문
 * - 자기 자신을 처리
 * - 오른쪽 자식 방문
 *
 * 3. 후위 순회 postorder
 * - 왼쪽 자식을 방문
 * - 오른쪽 자식 방문
 * - 자기 자신 처리
 *
 * */

public class Main {

    public static void main(String[] args) {
        BinaryTree binaryTree = new BinaryTree();
        binaryTree.insert(5); // root
        binaryTree.insert(7);
        binaryTree.insert(1);
        binaryTree.insert(3);
        binaryTree.insert(9);
        //binaryTree.preOrder(binaryTree.rootNode);
        //binaryTree.inOrder(binaryTree.rootNode);
        binaryTree.postOrder(binaryTree.rootNode);

    }
}

class Node {
    public int value;
    public Node leftChild;
    public Node rightChild;

    public Node(int value) {
        this.value = value;
    }
}

class BinaryTree {
    Node rootNode = null;

    public void insert(int ele) {
        if (rootNode == null) {
            rootNode = new Node(ele);
        } else {
            Node head = rootNode;
            Node currentNode;

            while (true) {
                currentNode = head;
                if (head.value > ele) {
                    head = head.leftChild;
                    if (head == null) {
                        currentNode.leftChild = new Node(ele);
                        break;
                    }
                } else {
                    head = head.rightChild;
                    if (head == null) {
                        currentNode.rightChild = new Node(ele);
                        break;
                    }
                }
            }

        }
    }


    /**
     * 1. 전위 순회 preorder
     * - 먼저 자기 자신을 처리
     * - 왼쪽 자식 방문
     * - 오른쪽 자식 방문
     * */
    public void preOrder(Node rootNode) {
        if (rootNode != null) {
            System.out.println(rootNode.value);
            preOrder(rootNode.leftChild);
            preOrder(rootNode.rightChild);
        }
    }


    /**
     * 2. 중위 순회 inorder
     * - 왼쪽 자식을 방문
     * - 자기 자신을 처리
     * - 오른쪽 자식 방문
     */
    public void inOrder(Node rootNode) {
        if (rootNode != null) {
            inOrder(rootNode.leftChild);
            System.out.println(rootNode.value);
            inOrder(rootNode.rightChild);
        }
    }

    /**
     * 3. 후위 순회 postorder
     * - 왼쪽 자식을 방문
     * - 오른쪽 자식 방문
     * - 자기 자신 처리
     */
    public void postOrder(Node rootNode) {
        if (rootNode != null) {
            postOrder(rootNode.leftChild);
            postOrder(rootNode.rightChild);
            System.out.println(rootNode.value);
        }
    }
}

```
