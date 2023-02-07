class AVLTreeNode<T: Comparable<T>>(var value: T) {
    var left: AVLTreeNode<T>? = null
    var right: AVLTreeNode<T>? = null
    var height = 1
}

class AVLTree<T: Comparable<T>> {
    private var root: AVLTreeNode<T>? = null

    private fun height(node: AVLTreeNode<T>?): Int {
        return node?.height ?: 0
    }

    private fun balanceFactor(node: AVLTreeNode<T>): Int {
        return height(node.right) - height(node.left)
    }

    private fun updateHeight(node: AVLTreeNode<T>) {
        node.height = maxOf(height(node.left), height(node.right)) + 1
    }

    private fun rightRotate(node: AVLTreeNode<T>): AVLTreeNode<T> {
        val x = node.left
        val T2 = x!!.right

        x.right = node
        node.left = T2

        updateHeight(node)
        updateHeight(x)

        return x
    }

    private fun leftRotate(node: AVLTreeNode<T>): AVLTreeNode<T> {
        val y = node.right
        val T2 = y!!.left

        y.left = node
        node.right = T2

        updateHeight(node)
        updateHeight(y)

        return y
    }

    private fun insert(node: AVLTreeNode<T>?, value: T): AVLTreeNode<T> {
        if (node == null) return AVLTreeNode(value)

        when {
            value < node.value -> node.left = insert(node.left, value)
            value > node.value -> node.right = insert(node.right, value)
            else -> return node
        }

        updateHeight(node)
        val balance = balanceFactor(node)

        return when {
            balance > 1 && value < node.right!!.value -> leftRotate(node)
            balance < -1 && value > node.left!!.value -> rightRotate(node)
            balance > 1 && value > node.right!!.value -> {
                node.right = rightRotate(node.right!!)
                leftRotate(node)
            }
            balance < -1 && value < node.left!!.value -> {
                node.left = leftRotate(node.left!!)
                rightRotate(node)
            }
            else -> node
        }
    }

    fun insert(value: T) {
        root = insert(root, value)
    }
}
