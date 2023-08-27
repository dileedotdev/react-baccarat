(Report written in Vietnamese)

## Tech stack
- React JS + Typescript + Vite.
- Tailwindcss for styling.
- Context API để quản lý global state.
  
## UI
- Bàn chơi để hiển thị thông tin về người chơi và lá bài. 
- Thông tin của mỗi người chơi: Tên, Coins, Point of 3 Card, Lá bài khi nhận. 
- Khu vực hiển thị Deck Cards (số lá bài còn lại). 
- Các nút: Shuffle, Drawn, Reveal, Reset.

## States
- Remaining cards: số lá bài còn lại trong deck.
- Desk id: id của deck hiện tại.
- Player Coins: số coins của người chơi (default: 5000/player).
- Player Cards: lá bài hiện tại của người chơi.

## Phân tích chức năng

### Shuffle
- Gọi API deckofcardsapi để tạo một desk mới
- Cập nhật state "Desk id" là kết quả api call
- Cập nhật state "Remaining cards" là 52

### Drawn
- Kiểm tra state "Remaining cards" có còn lớn hơn 12 không (nếu không thông báo cho người chơi)
- Gọi API deckofcardsapi chia bài 4 lần, mỗi lần 3 lá để chia bài cho 4 người chơi
- Trừ state "Remaining cards" đi 12
- Cập nhật state "Player Cards" là các lá bài trả về từ api call

### Reveal
- Hiện thị các lá bài mà người dùng đang giữ.
- Tính điểm cho tất cả người chơi và xét ai thắng ai thua.
- Trừ 900 coins mỗi người thua và chia số coins thu được cho người thắng.
- Cập nhật state "Player Coins" của mỗi người chơi người chơi
- Thông báo cho người chơi

### Reset
- Cập nhật lại các states về mặc định
