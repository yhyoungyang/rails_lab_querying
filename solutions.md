## Solutions

1) Get a list of all tow trucks.

`TowTruck.all`

2) Get the vehicle with ID 3.

`Vehicle.find(3)`

3) Get the vehicle with VIN D0985DF1593A350A4.

`Vehicle.find_by(vin: 'D0985DF1593A350A4')`

4) Get a list of all vehicles sorted by acquisition date.

`Vehicle.order(:acquired_at)`

5) Get a list of all silver vehicles, ordered alphabetically by make.

`Vehicle.where(color: 'silver').order(:make)`

6) Get a list of all red Honda vehicles that are cars.

`Vehicle.where(make: 'Honda', color: 'red', category: 'car')`

7) Get a count of all vehicles that are motorcycles.

`Vehicle.where(category: 'motorcycle').count`

8) Get a count of vehicles that are currently on the lot (i.e. not released).

`Vehicle.where(released_at: nil).count`

9) Get a list of all tow trucks whose mileage is over 200,000.

`TowTruck.where('mileage > ?', 200_000)`

10) Get a list of all tow trucks whose last service was more than 8 months ago.

`TowTruck.where('last_service_at < ?', 8.months.ago)`

11) Get the average tow fee across all vehicles.

`Vehicle.average(:fee).to_s`

12) Get the top 3 vehicles with the highest tow fees.

`Vehicle.where.not(fee: nil).order(fee: :desc).limit(3)`

13) Get all vehicles that have a fee assessed which has not been paid.

`Vehicle.where(is_paid: false).where.not(fee: nil)`

14) Get a list of all released vehicles, sorted by most recently released.

`Vehicle.where.not(released_at: nil).order(released_at: :desc)`

15) Get a list of all vehicles that have notes.

`Vehicle.where.not(notes: [nil, ''])`

16) Get the VINs of all vehicles manufactured before the year 2000.

`Vehicle.where('year < ?', 2000).pluck(:vin)`

17) Get the make, model, and year of all silver vehicles, ordered by year.

`Vehicle.where(color: 'silver').order(:year).pluck(:year, :make, :model)`

18) Get the total income from all vehicles (i.e. sum of all fees that are paid).

`Vehicle.where(is_paid: true).sum(:fee).to_s`
