# HotelMain.py

from enum import Enum

class LoyaltyStatus(Enum):
    NONE = "None"
    BRONZE = "Bronze"
    SILVER = "Silver"
    GOLD = "Gold"

class PaymentMethod(Enum):
    CREDIT_CARD = "Credit Card"
    BANK_TRANSFER = "Bank Transfer"

class Hotel:
    def __init__(self, hotel_name, location, total_rooms, available_rooms):
        self._hotel_name = hotel_name
        self._location = location
        self._total_rooms = total_rooms
        self._available_rooms = available_rooms

    def get_hotel_name(self): return self._hotel_name
    def set_hotel_name(self, hotel_name): self._hotel_name = hotel_name
    def get_location(self): return self._location
    def set_location(self, location): self._location = location
    def get_total_rooms(self): return self._total_rooms
    def set_total_rooms(self, total_rooms): self._total_rooms = total_rooms
    def get_available_rooms(self): return self._available_rooms
    def set_available_rooms(self, available_rooms): self._available_rooms = available_rooms
    def display_hotel_info(self): return f"Hotel: {self._hotel_name}, Location: {self._location}, Total Rooms: {self._total_rooms}, Available Rooms: {self._available_rooms}"

class Review:
    def __init__(self, review_id, rating, feedback_comment, review_date):
        self._review_id = review_id
        self._rating = rating
        self._feedback_comment = feedback_comment
        self._review_date = review_date

    def get_review_id(self): return self._review_id
    def set_review_id(self, review_id): self._review_id = review_id
    def get_rating(self): return self._rating
    def set_rating(self, rating): self._rating = rating
    def get_feedback_comment(self): return self._feedback_comment
    def set_feedback_comment(self, feedback_comment): self._feedback_comment = feedback_comment
    def get_review_date(self): return self._review_date
    def set_review_date(self, review_date): self._review_date = review_date
    def display_feedback_and_reviews_info(self): return f"Review ID: {self._review_id}, Rating: {self._rating}, Comment: {self._feedback_comment}, Date: {self._review_date}"

class Room:
    def __init__(self, room_number, room_type, price, availability_status, amenities):
        self._room_number = room_number
        self._room_type = room_type
        self._price = price
        self._availability_status = availability_status
        self._amenities = amenities

    def get_room_number(self): return self._room_number
    def set_room_number(self, room_number): self._room_number = room_number
    def get_room_type(self): return self._room_type
    def set_room_type(self, room_type): self._room_type = room_type
    def get_price(self): return self._price
    def set_price(self, price): self._price = price
    def get_availability_status(self): return self._availability_status
    def set_availability_status(self, availability_status): self._availability_status = availability_status
    def get_amenities(self): return self._amenities
    def set_amenities(self, amenities): self._amenities = amenities
    def display_room_info(self): return f"Room Number: {self._room_number}, Type: {self._room_type}, Price: {self._price}, Availability: {self._availability_status}, Amenities: {self._amenities}"

class DoubleRoom(Room):
    def __init__(self, room_number, price, availability_status, amenities, has_king_size_bed, has_balcony):
        super().__init__(room_number, "Double", price, availability_status, amenities)
        self._has_king_size_bed = has_king_size_bed
        self._has_balcony = has_balcony

    def get_has_king_size_bed(self): return self._has_king_size_bed
    def set_has_king_size_bed(self, has_king_size_bed): self._has_king_size_bed = has_king_size_bed
    def get_has_balcony(self): return self._has_balcony
    def set_has_balcony(self, has_balcony): self._has_balcony = has_balcony
    def display_double_room_info(self): return f"{super().display_room_info()}, King Size Bed: {self._has_king_size_bed}, Balcony: {self._has_balcony}"

class SingleRoom(Room):
    def __init__(self, room_number, price, availability_status, amenities, has_work_desk, has_mini_fridge):
        super().__init__(room_number, "Single", price, availability_status, amenities)
        self._has_work_desk = has_work_desk
        self._has_mini_fridge = has_mini_fridge

    def get_has_work_desk(self): return self._has_work_desk
    def set_has_work_desk(self, has_work_desk): self._has_work_desk = has_work_desk
    def get_has_mini_fridge(self): return self._has_mini_fridge
    def set_has_mini_fridge(self, has_mini_fridge): self._has_mini_fridge = has_mini_fridge
    def display_single_room_info(self): return f"{super().display_room_info()}, Work Desk: {self._has_work_desk}, Mini Fridge: {self._has_mini_fridge}"

class Guest:
    def __init__(self, guest_id, guest_name, contact_information, loyalty_status, reservations=None):
        if reservations is None:
            reservations = []
        self._guest_id = guest_id
        self._guest_name = guest_name
        self._contact_information = contact_information
        self._loyalty_status = loyalty_status
        self._reservations = reservations

    def get_guest_id(self): return self._guest_id
    def set_guest_id(self, guest_id): self._guest_id = guest_id
    def get_guest_name(self): return self._guest_name
    def set_guest_name(self, guest_name): self._guest_name = guest_name
    def get_contact_information(self): return self._contact_information
    def set_contact_information(self, contact_information): self._contact_information = contact_information
    def get_loyalty_status(self): return self._loyalty_status
    def set_loyalty_status(self, loyalty_status): self._loyalty_status = loyalty_status
    def get_reservations(self): return self._reservations
    def set_reservations(self, reservations): self._reservations = reservations
    def add_reservation(self, booking): self._reservations.append(booking)
    def display_guest_info(self): return f"Guest ID: {self._guest_id}, Name: {self._guest_name}, Contact: {self._contact_information}, Loyalty: {self._loyalty_status.value}"

class Booking:
    def __init__(self, guest, rooms, check_in, check_out, status, payment):
        self._guest = guest
        self._rooms = rooms
        self._check_in = check_in
        self._check_out = check_out
        self._status = status
        self._payment = payment

    def get_guest(self): return self._guest
    def set_guest(self, guest): self._guest = guest
    def get_rooms(self): return self._rooms
    def set_rooms(self, rooms): self._rooms = rooms
    def get_check_in(self): return self._check_in
    def set_check_in(self, check_in): self._check_in = check_in
    def get_check_out(self): return self._check_out
    def set_check_out(self, check_out): self._check_out = check_out
    def get_status(self): return self._status
    def set_status(self, status): self._status = status
    def get_payment(self): return self._payment
    def set_payment(self, payment): self._payment = payment
    def confirm_booking(self): self._status = "Confirmed"
    def cancel_booking(self): self._status = "Cancelled"
    def display_booking(self): return f"Booking for {self._guest.get_guest_name()}, Rooms: {[room.get_room_number() for room in self._rooms]}, Check-in: {self._check_in}, Check-out: {self._check_out}, Status: {self._status}"

class LoyaltyProgram:
    def __init__(self, program_id, points_balance, available_rewards, points_expiration, guest):
        self._program_id = program_id
        self._points_balance = points_balance
        self._available_rewards = available_rewards
        self._points_expiration = points_expiration
        self._guest = guest

    def get_program_id(self): return self._program_id
    def set_program_id(self, program_id): self._program_id = program_id
    def get_points_balance(self): return self._points_balance
    def set_points_balance(self, points_balance): self._points_balance = points_balance
    def get_available_rewards(self): return self._available_rewards
    def set_available_rewards(self, available_rewards): self._available_rewards = available_rewards
    def get_points_expiration(self): return self._points_expiration
    def set_points_expiration(self, points_expiration): self._points_expiration = points_expiration
    def get_guest(self): return self._guest
    def set_guest(self, guest): self._guest = guest
    def add_rewards(self, points): self._points_balance += points
    def redeem_rewards(self, reward): return f"Rewards redeemed: {reward}"
    def display_loyalty_awards_info(self): return f"Program ID: {self._program_id}, Points: {self._points_balance}, Rewards: {self._available_rewards}, Expiration: {self._points_expiration}, Guest: {self._guest.get_guest_name()}"

class Invoice:
    def __init__(self, invoice_id, booking, total_amount, vat, payment_status):
        self._invoice_id = invoice_id
        self._booking = booking
        self._total_amount = total_amount
        self._vat = vat
        self._payment_status = payment_status

    def get_invoice_id(self): return self._invoice_id
    def set_invoice_id(self, invoice_id): self._invoice_id = invoice_id
    def get_booking(self): return self._booking
    def set_booking(self, booking): self._booking = booking
    def get_total_amount(self): return self._total_amount
    def set_total_amount(self, total_amount): self._total_amount = total_amount
    def get_vat(self): return self._vat
    def set_vat(self, vat): self._vat = vat
    def get_payment_status(self): return self._payment_status
    def set_payment_status(self, payment_status): self._payment_status = payment_status
    def generate_invoice_details(self): return f"Total: {self._total_amount + self._vat}"
    def display_invoice_info(self): return f"Invoice ID: {self._invoice_id}, Booking: {self._booking.display_booking()}, Total: {self.generate_invoice_details()}, Status: {self._payment_status}"

class Payment:
    def __init__(self, booking, payment_method, amount_paid, invoice_number):
        self._booking = booking
        self._payment_method = payment_method
        self._amount_paid = amount_paid
        self._invoice_number = invoice_number

    def get_booking(self): return self._booking
    def set_booking(self, booking): self._booking = booking
    def get_payment_method(self): return self._payment_method
    def set_payment_method(self, payment_method): self._payment_method = payment_method
    def get_amount_paid(self): return self._amount_paid
    def set_amount_paid(self, amount_paid): self._amount_paid = amount_paid
    def get_invoice_number(self): return self._invoice_number
    def set_invoice_number(self, invoice_number): self._invoice_number = invoice_number
    def process_payment(self): return True
    def display_payment(self): return f"Payment Method: {self._payment_method.value}, Amount: {self._amount_paid}, Invoice: {self._invoice_number}"

class BankTransferPayment(Payment):
    def __init__(self, booking, amount_paid, invoice_number, bank_name, account_number):
        super().__init__(booking, PaymentMethod.BANK_TRANSFER, amount_paid, invoice_number)
        self._bank_name = bank_name
        self._account_number = account_number

    def get_bank_name(self): return self._bank_name
    def set_bank_name(self, bank_name): self._bank_name = bank_name
    def get_account_number(self): return self._account_number
    def set_account_number(self, account_number): self._account_number = account_number
    def validate_payment(self): return True
    def display_bank_transfer_payment(self): return f"{super().display_payment()}, Bank: {self._bank_name}, Account: {self._account_number}"

class CreditCardPayment(Payment):
    def __init__(self, booking, amount_paid, invoice_number, card_number, expiry_date):
        super().__init__(booking, PaymentMethod.CREDIT_CARD, amount_paid, invoice_number)
        self._card_number = card_number
        self._expiry_date = expiry_date

    def get_card_number(self): return self._card_number
    def set_card_number(self, card_number): self._card_number = card_number
    def get_expiry_date(self): return self._expiry_date
    def set_expiry_date(self, expiry_date): self._expiry_date = expiry_date
    def validate_payment(self): return True
    def display_credit_card_payment(self): return f"{super().display_payment()}, Card: {self._card_number}, Expiry: {self._expiry_date}"

# HotelSystemTesting.py

# Sample stored staff credentials
stored_staff_id = "Dhabia"
stored_staff_password = "Dhabia604"

# Staff login loop
while True:
    print("===== Hotel Management System - Staff Login =====")
    staff_id = input("Enter your staff ID: ")
    password = input("Enter your password: ")
    if staff_id == stored_staff_id and password == stored_staff_password:
        print("Login successful. Welcome, Staff!\n")
        break
    else:
        print("Incorrect staff ID or password. Please try again.\n")

# === Test 1: Guest Account Creation ===
print("\n==================== Test 1: Guest Account Creation ====================")
try:
    guest1 = Guest("G001", "Afrah", "Afrah@gmail.com", LoyaltyStatus.GOLD, [])
    guest2 = Guest("G002", "Aysha", "Aysha@gmail.com", LoyaltyStatus.SILVER, [])
    print(guest1.display_guest_info())
    print(guest2.display_guest_info())
    guest3 = Guest("G003", "Shamma", "Shamma@gmail.com", LoyaltyStatus.BRONZE, [])
    guest4 = Guest("G004", "Haya", "Haya@gmail.com", LoyaltyStatus.NONE, [])
    print(guest3.display_guest_info())
    print(guest4.display_guest_info())
except Exception as e:
    print(f"[Error] Test 1 - Guest creation failed: {type(e).__name__} - {e}")

# === Test 2: Searching for Available Rooms ===
print("\n==================== Test 2: Searching for Available Rooms ====================")
try:
    hotel = Hotel("Royal Stay", "Abu Dhabi", 100, 50)
    room1 = DoubleRoom(201, 350.0, "Available", ["WiFi", "TV"], True, True)
    room2 = SingleRoom(202, 200.0, "Unavailable", ["WiFi"], True, False)
    room3 = DoubleRoom(203, 400.0, "Available", ["WiFi","Balcony"], True, True)
    room4 = SingleRoom(204, 250.0, "Available", ["Mini Fridge"], True, False)
    available_rooms1 = [room for room in [room1, room2] if room.get_availability_status() == "Available"]
    available_rooms2 = [room for room in [room3, room4] if room.get_availability_status() == "Available"]
    print("\nAvailable Rooms Set 1:")
    for room in available_rooms1:
        print(room.display_room_info())
    print("\nAvailable Rooms Set 2:")
    for room in available_rooms2:
        print(room.display_room_info())
except Exception as e:
    print(f"[Error] Test 2 - Room search failed: {type(e).__name__} - {e}")

# === Test 3: Making a Room Reservation ===
print("\n==================== Test 3: Making a Room Reservation ====================")
try:
    roomA = SingleRoom(101, 250.0, "Available", ["WiFi", "Mini Fridge"], True, False)
    roomB = DoubleRoom(102, 400.0, "Available", ["WiFi", "Balcony"], True, True)
    booking1 = Booking(guest1, [roomA], "2025-04-01", "2025-04-05", "Pending", None)
    booking2 = Booking(guest2, [roomB], "2025-04-10", "2025-04-12", "Pending", None)
    guest1.add_reservation(booking1)
    guest2.add_reservation(booking2)
    print(booking1.display_booking())
    print(booking2.display_booking())
    roomC = SingleRoom(103, 300.0, "Available", ["Work Desk"], True, False)
    roomD = DoubleRoom(104, 500.0, "Available", ["Pool View"], True, True)
    booking3 = Booking(guest3, [roomC], "2025-05-01", "2025-05-03", "Pending", None)
    booking4 = Booking(guest4, [roomD], "2025-05-05", "2025-05-07", "Pending", None)
    guest3.add_reservation(booking3)
    guest4.add_reservation(booking4)
    print(booking3.display_booking())
    print(booking4.display_booking())
except Exception as e:
    print(f"[Error] Test 3 - Room reservation failed: {type(e).__name__} - {e}")

# === Test 4: Booking Confirmation Notification (Status Update) ===
print("\n==================== Test 4: Booking Confirmation Notification ====================")
try:
    booking1.confirm_booking()
    booking2.confirm_booking()
    print("Booking 1 Status:", booking1.get_status())
    print("Booking 2 Status:", booking2.get_status())
    booking3.confirm_booking()
    booking4.confirm_booking()
    print("Booking 3 Status:", booking3.get_status())
    print("Booking 4 Status:", booking4.get_status())
except Exception as e:
    print(f"[Error] Test 4 - Booking confirmation failed: {type(e).__name__} - {e}")

# === Test 5: Invoice Generation for a Booking ===
print("\n==================== Test 5: Invoice Generation for a Booking ====================")
try:
    invoice1 = Invoice("INV301", booking1, 1400.0, 70.0, "Paid")
    invoice2 = Invoice("INV302", booking2, 400.0, 20.0, "Paid")
    print(invoice1.display_invoice_info())
    print(invoice2.display_invoice_info())
    invoice3 = Invoice("INV303", booking3, 600.0, 30.0, "Paid")
    invoice4 = Invoice("INV304", booking4, 1000.0, 50.0, "Paid")
    print(invoice3.display_invoice_info())
    print(invoice4.display_invoice_info())
except Exception as e:
    print(f"[Error] Test 5 - Invoice generation failed: {type(e).__name__} - {e}")

# === Test 6: Processing Different Payment Methods ===
print("\n==================== Test 6: Processing Different Payment Methods ====================")
try:
    payment1 = CreditCardPayment(booking1, 1400.0, "INV301", "1234-5678-9012-3456", "12/25")
    payment2 = BankTransferPayment(booking2, 400.0, "INV302", "Abu Dhabi Bank", "123456789")
    print(payment1.display_credit_card_payment())
    print(payment2.display_bank_transfer_payment())
    payment3 = CreditCardPayment(booking3, 600.0, "INV303", "5678-9012-3456-1234", "01/26")
    payment4 = BankTransferPayment(booking4, 1000.0, "INV304", "Abu Dhabi Bank", "9876543210")
    print(payment3.display_credit_card_payment())
    print(payment4.display_bank_transfer_payment())
except Exception as e:
    print(f"[Error] Test 6 - Payment processing failed: {type(e).__name__} - {e}")

# === Test 7: Displaying Reservation History ===
print("\n==================== Test 7: Displaying Reservation History ====================")
try:
    print(f"Reservations for {guest1.get_guest_name()}:")
    for booking in guest1.get_reservations():
        print(booking.display_booking())
    print(f"Reservations for {guest2.get_guest_name()}:")
    for booking in guest2.get_reservations():
        print(booking.display_booking())
    print(f"Reservations for {guest3.get_guest_name()}:")
    for booking in guest3.get_reservations():
        print(booking.display_booking())
    print(f"Reservations for {guest4.get_guest_name()}:")
    for booking in guest4.get_reservations():
        print(booking.display_booking())
except Exception as e:
    print(f"[Error] Test 7 - Displaying reservation history failed: {type(e).__name__} - {e}")

# === Test 8: Cancellation of a Reservation ===
print("\n==================== Test 8: Cancellation of a Reservation ====================")
try:
    print("[Before Cancellation] Booking 2:")
    print(booking2.display_booking())
    booking2.cancel_booking()
    print("\n[After Cancellation] Booking 2:")
    print(booking2.display_booking())
    print("\n[Before Cancellation] Booking 4:")
    print(booking4.display_booking())
    booking4.cancel_booking()
    print("\n[After Cancellation] Booking 4:")
    print(booking4.display_booking())
except Exception as e:
    print(f"[Error] Test 8 - Cancellation failed: {type(e).__name__} - {e}")
