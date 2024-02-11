Orginial qb-truckrobbery here https://github.com/qbcore-framework/qb-truckrobbery
<BR>
<BR> I added this code block to client.lua this fixes the bug where nothing happens when you need to silence the alarm

```lua
-- Function to make guards exit the truck
function MakeGuardsExitTruck()
    local pilotSeat = GetPedInVehicleSeat(transport, -1)
    local navigatorSeat = GetPedInVehicleSeat(transport, 0)

    if pilotSeat ~= nil and navigatorSeat ~= nil then
        TaskLeaveVehicle(pilotSeat, transport, 0)
        TaskLeaveVehicle(navigatorSeat, transport, 0)
        Citizen.Wait(1000) -- Wait for a second for guards to exit the truck
        TaskCombatPed(pilotSeat, PlayerPedId(), 0, 16)
        TaskCombatPed(navigatorSeat, PlayerPedId(), 0, 16)
        AreGuardsOutside = true
    end
end
```
