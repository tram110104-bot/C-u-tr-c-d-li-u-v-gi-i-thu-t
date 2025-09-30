#C-u-tr-c-d-li-u-v-gi-i-thu
# Định nghĩa một nút trong danh sách liên kết đơn
class Node:
    def __init__(self, data):
        self.data = data      # Lưu dữ liệu của nút
        self.next = None      # Con trỏ trỏ đến nút tiếp theo (ban đầu là None)


# Định nghĩa lớp Singly Linked List
class SinglyLinkedList:
    def __init__(self):
        self.head = None      # Con trỏ đầu danh sách (ban đầu rỗng)

    # Thêm nút mới vào cuối danh sách
    def append(self, data):
        new_node = Node(data)     # Tạo một nút mới
        if self.head is None:     # Nếu danh sách rỗng
            self.head = new_node  # Gán head = new_node
            return
        current = self.head       # Bắt đầu từ head
        while current.next:       # Duyệt đến nút cuối
            current = current.next
        current.next = new_node   # Nối new_node vào cuối

    # Thêm nút mới vào đầu danh sách
    def prepend(self, data):
        new_node = Node(data)     # Tạo nút mới
        new_node.next = self.head # Cho new_node trỏ đến head cũ
        self.head = new_node      # Cập nhật head = new_node

    # Xóa nút theo giá trị
    def delete(self, key):
        current = self.head

        # Nếu danh sách rỗng
        if current is None:
            return

        # Nếu nút đầu chứa giá trị cần xóa
        if current.data == key:
            self.head = current.next   # Bỏ qua nút đầu
            current = None
            return

        # Duyệt danh sách để tìm nút cần xóa
        prev = None
        while current and current.data != key:
            prev = current
            current = current.next

        # Nếu không tìm thấy
        if current is None:
            return

        # Bỏ qua nút cần xóa
        prev.next = current.next
        current = None

    # In danh sách ra màn hình
    def print_list(self):
        current = self.head
        while current:
            print(current.data, end=" -> ")
            current = current.next
        print("None")


# ======= Demo =======
ll = SinglyLinkedList()
ll.append(10)
ll.append(20)
ll.append(30)
ll.prepend(5)
ll.print_list()    # 5 -> 10 -> 20 -> 30 -> None

ll.delete(20)
ll.print_list()    # 5 -> 10 -> 30 -> None
