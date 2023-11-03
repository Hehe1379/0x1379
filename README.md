# 0x1379
starting to study

#录入的UTF-8文本转换为十六进制格式 2023/11/03 08/44
import tkinter as tk

def convert_to_hex():
    utf8_text = text_entry.get("1.0", "end-1c")
    hex_text = utf8_text.encode("utf-8").hex()
    hex_text_with_prefix = "0x" + hex_text  # 添加"0x"前缀
    hex_output.delete("1.0", "end")
    hex_output.insert("1.0", hex_text_with_prefix)

def copy_to_clipboard():
    hex_text = hex_output.get("1.0", "end-1c")
    hex_text = hex_text.strip().replace(" ", "")  # 移除空格和换行符
    window.clipboard_clear()  # 清空剪贴板内容
    window.clipboard_append(hex_text)  # 将十六进制文本添加到剪贴板

# 创建窗口
window = tk.Tk()
window.title("UTF-8 to Hex Converter")

# 创建文本输入框
text_entry = tk.Text(window, height=5, width=40)
text_entry.pack()

# 创建复制按钮
copy_button = tk.Button(window, text="Copy", command=copy_to_clipboard)
copy_button.pack()

# 创建十六进制输出框
hex_output = tk.Text(window, height=5, width=40)
hex_output.pack()

# 绑定实时转换和复制按钮
text_entry.bind("<KeyRelease>", lambda event: convert_to_hex())
copy_button.config(command=copy_to_clipboard)

# 运行窗口主循环
window.mainloop()
