#include 	<amxmodx>
#include	<cstrike>

#define 	PLUGIN 								"InfiniteAmmo"
#define 	VERSION 							"V1.0"
#define 	AUTHOR 								"EOS"

public plugin_init() 
{
	register_plugin(PLUGIN, VERSION, AUTHOR)
	
	// Registering an event OnPlayerHoldWeapon 
	
	register_event("CurWeapon", "OnPlayerHoldWeapon", "be", "1=1")
}

// The WeaponInfo enumerator stores information GunID, GunAmmo which is needed for the E_WeaponsIDs array

enum WeaponInfo
{
	WeaponID,
	WeaponAmmo
}

// Creating an array E_WeaponsIDs that stores weapons and also, the standard value of cartridges in the magazine's stock

new const E_WeaponsIDs[][WeaponInfo] = 
{
	{CSW_M249, 200}, {CSW_GLOCK18, 90}, {CSW_AK47, 90}, {CSW_M4A1, 90}, {CSW_P90, 50}, {CSW_TMP, 90}, {CSW_G3SG1, 80}, {CSW_DEAGLE, 32}, 
	{CSW_SG552, 90}, {CSW_M3, 24}, {CSW_MP5NAVY, 90}, {CSW_USP, 36}, {CSW_FAMAS, 75}, {CSW_GALIL, 105}, {CSW_SG550, 90}, {CSW_UMP45, 90}, 
	{CSW_FIVESEVEN, 60}, {CSW_ELITE, 90}, {CSW_AUG, 90}, {CSW_MAC10, 90}, {CSW_XM1014, 21}, {CSW_SCOUT, 30}, {CSW_AWP, 30}, {CSW_GLOCK18, 60}, 
	{CSW_P228, 60}
}

// Callback OnPlayerHoldWeapon responsible for updating the weapon data of the holding player

public OnPlayerHoldWeapon(id)
{
	// We receive data from the CurWeapon event such as: isactive - whether the player is holding a weapon in his hands
	new 
		isactive = read_data(1)
	
	if(isactive)
	{
		// weaponid - ID Weapon player which he holds in his hands
		new 
			weaponid = read_data(2)
		for(new i; i < sizeof E_WeaponsIDs; i++)
		{
			// Does the ID of the player's Weapon in the E_WeaponsIDs array match?
			if(weaponid == E_WeaponsIDs[i][WeaponID])
				// We install cartridges in the stock of the store, previously indicated to us in E_WeaponsIDs
				cs_set_user_bpammo(id, weaponid, E_WeaponsIDs[i][WeaponAmmo])	
		}
	}
}
