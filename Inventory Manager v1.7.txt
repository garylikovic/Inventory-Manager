<#
    Inventory Manager Version 2.5
    Created by: Gary Likovic





#>

Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

#  Functions Section--------------------------------------------------
function NewCItem {

if($global:Database -eq '$PSScriptRoot\data\console_database.csv') {    
    ",,,,,,,,,," | Out-File $PSScriptRoot\data\console_database.csv -Append -Encoding utf8
    "[ITEM ADDED] | New Console Item Added |" | Out-File $DailyActionReport -Append
    PopulateConsoles
}

elseif($global:Database -eq '$PSScriptRoot\data\game_database.csv') {
    ",,,,,,,,,,," | Out-File $PSScriptRoot\data\game_database.csv -Append -Encoding utf8
    "[ITEM ADDED] | New Game Item Added |" | Out-File $DailyActionReport -Append
    PopulateGames
}  

elseif($global:Database -eq '$PSScriptRoot\data\access_database.csv'){
    ",,,,,,,," | Out-File $PSScriptRoot\data\access_database.csv -Append -Encoding utf8
    "[ITEM ADDED] | New Accessory Item Added |" | Out-File $DailyActionReport -Append
    AccessoriesButton
}
elseif($global:Database -eq '$PSScriptRoot\data\bluray_database.csv'){ 
    ",,,,,,,,,,," | Out-File $PSScriptRoot\data\bluray_database.csv -Append -Encoding utf8
    "[ITEM ADDED] | New BluRay Item Added |" | Out-File $DailyActionReport -Append
    PopulateBluRay
}
elseif($global:Database -eq '$PSScriptRoot\data\collectable_database.csv'){ 
    ",,,,,,,,,," | Out-File $PSScriptRoot\data\collectable_database.csv -Append -Encoding utf8
    "[ITEM ADDED] | New BluRay Item Added |" | Out-File $DailyActionReport -Append
    PopulateCollectables
}
elseif($global:Database -eq '$PSScriptRoot\data\SellerID_database.csv'){
    ",,,,,," | Out-File $PSScriptRoot\data\SellerID_database.csv -Append -Encoding utf8
    "[ITEM ADDED] | New Seller ID Added |" | Out-File $DailyActionReport -Append
    SellerIDList
}



else{}

}

function PopulateConsoles{

"[LIST LOADED] | Populated Console List |" | Out-File $DailyActionReport -Append

#------Function for Populating the Rows--------------
$global:Database = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.Sold -ne "Y"}
$array = New-Object System.Collections.ArrayList
$data = @($global:Database)
$array.AddRange($data)
$datagridview.DataSource = $array
$global:Database = '$PSScriptRoot\data\console_database.csv'
#----------------------------------------------------

	$consolecheckBox.Visible = $true
	$consolecheckBox.Location = New-Object System.Drawing.Point(550,220)

	$PricecheckBox.Visible = $true
	$PricecheckBox.Location = New-Object System.Drawing.Point(550,240)

	$ConsoleModelcheckBox.Visible = $true
	$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(550,260)

	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,280)

	$SerialNumbercheckBox.Visible = $true
	$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(550,300)
	
	
	$ratingcheckBox.Visible = $false
	$gamenamecheckBox.Visible = $false
	$GameRegioncheckBox.Visible = $false
	$CompatcheckBox.Visible = $false
    $TitleNameCBox.Location = New-Object System.Drawing.Point(550,220)
    $TitleNameCBox.Visible = $false
    $ItemNameCBox.Visible = $false
    $FormatcheckBox.Visible = $false

}

function PopulateBluRay {

"[LIST LOADED] | Populated BluRay List |" | Out-File $DailyActionReport -Append

#------Function for Populating the Rows--------------
$global:Database = Import-CSV $PSScriptRoot\data\bluray_database.csv | where {$_.Sold -ne "Y"}
$array = New-Object System.Collections.ArrayList
$data = @($global:Database)
$array.AddRange($data)
$datagridview.DataSource = $array
$global:Database = '$PSScriptRoot\data\bluray_database.csv'
#----------------------------------------------------

	$PricecheckBox.Visible = $true
	$PricecheckBox.Location = New-Object System.Drawing.Point(550,240)
	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,260)
    $TitleNameCBox.Location = New-Object System.Drawing.Point(550,220)
    $TitleNameCBox.Visible = $true
    $FormatcheckBox.Visible = $true

	$consolecheckBox.Visible = $false
	$consolecheckBox.Location = New-Object System.Drawing.Point(540,220)
	$CompatcheckBox.Visible = $false
	$CompatcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$gamenamecheckBox.Visible = $false
	$gamenamecheckBox.Location = New-Object System.Drawing.Point(540,260)
	$ratingcheckBox.Visible = $false
	$ratingcheckBox.Location = New-Object System.Drawing.Point(650,220)
	$ConsoleModelcheckBox.Visible = $false
	$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$SerialNumbercheckBox.Visible = $false
	$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(540,300)
        $ItemNameCBox.Visible = $false

}

function PopulateGames{

"[LIST LOADED] | Populated Games List |" | Out-File $DailyActionReport -Append

#------Function for Populating the Rows--------------
$global:Database = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.Sold -ne "Y"}
$array = New-Object System.Collections.ArrayList
$data = @($global:Database)
$array.AddRange($data)
$datagridview.DataSource = $array
$global:Database = '$PSScriptRoot\data\game_database.csv'
#----------------------------------------------------
	$consolecheckBox.Visible = $true
	$consolecheckBox.Location = New-Object System.Drawing.Point(550,220)
	$PricecheckBox.Visible = $true
	$PricecheckBox.Location = New-Object System.Drawing.Point(550,240)
	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,280)
	$ratingcheckBox.Visible = $true
	$ratingcheckBox.Location = New-Object System.Drawing.Point(550,220)
	$gamenamecheckBox.Visible = $true
	$gamenamecheckBox.Location = New-Object System.Drawing.Point(550,260)
	$GameRegioncheckBox.Visible = $true
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(550,300)
	$CompatcheckBox.Visible = $true
	$CompatcheckBox.Location = New-Object System.Drawing.Point(550,240)
	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,280)

	$ConsoleModelcheckBox.Visible = $false
	$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$SerialNumbercheckBox.Visible = $false
	$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(540,300)
    $ItemNameCBox.Visible = $false
    $TitleNameCBox.Visible = $false
    $FormatcheckBox.Visible = $false
}

function PopulateCollectables {

"[LIST LOADED] | Populated Collectables List |" | Out-File $DailyActionReport -Append

#------Function for Populating the Rows--------------
$global:Database = Import-CSV $PSScriptRoot\data\collectable_database.csv | where {$_.Sold -ne "Y"}
$array = New-Object System.Collections.ArrayList
$data = @($global:Database)
$array.AddRange($data)
$datagridview.DataSource = $array
$global:Database = '$PSScriptRoot\data\collectable_database.csv'
#----------------------------------------------------


	$PricecheckBox.Visible = $true
	$PricecheckBox.Location = New-Object System.Drawing.Point(550,240)
	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,260)
    $ItemNameCBox.Visible = $true
    $FormatcheckBox.Visible = $true

	$consolecheckBox.Visible = $false
	$consolecheckBox.Location = New-Object System.Drawing.Point(540,220)
	$CompatcheckBox.Visible = $false
	$CompatcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$gamenamecheckBox.Visible = $false
	$gamenamecheckBox.Location = New-Object System.Drawing.Point(540,260)
	$ratingcheckBox.Visible = $false
	$ratingcheckBox.Location = New-Object System.Drawing.Point(650,220)
	$ConsoleModelcheckBox.Visible = $false
	$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$SerialNumbercheckBox.Visible = $false
	$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(540,300)
    $TitleNameCBox.Visible = $false
    
}

function AccessoriesButton {

"[LIST LOADED] | Populated Accessory List |" | Out-File $DailyActionReport -Append

#------Function for Populating the Rows--------------
$global:Database = Import-CSV $PSScriptRoot\data\access_database.csv | where {$_.Sold -ne "Y"}
$array = New-Object System.Collections.ArrayList
$data = @($global:Database)
$array.AddRange($data)
$datagridview.DataSource = $array
$global:Database = '$PSScriptRoot\data\access_database.csv'
#----------------------------------------------------

	$consolecheckBox.Visible = $true
	$consolecheckBox.Location = New-Object System.Drawing.Point(550,220)
	$PricecheckBox.Visible = $true
	$PricecheckBox.Location = New-Object System.Drawing.Point(550,240)
	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,280)
	$CompatcheckBox.Visible = $true
	$CompatcheckBox.Location = New-Object System.Drawing.Point(550,260)
	$ConditioncheckBox.Visible = $true
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(550,280)

	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$gamenamecheckBox.Visible = $false
	$gamenamecheckBox.Location = New-Object System.Drawing.Point(540,260)
	$ratingcheckBox.Visible = $false
	$ratingcheckBox.Location = New-Object System.Drawing.Point(650,220)
	$ConsoleModelcheckBox.Visible = $false
	$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$SerialNumbercheckBox.Visible = $false
	$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(540,300)
    $TitleNameCBox.Visible = $false
    $ItemNameCBox.Visible = $false
    $FormatcheckBox.Visible = $false


}

function SellerIDList {

"[LIST LOADED] | Populated Seller ID List |" | Out-File $DailyActionReport -Append

#------Function for Populating the Rows--------------
$global:Database = Import-CSV $PSScriptRoot\data\SellerID_database.csv | where {$_.Sold -ne "Y"}
$array = New-Object System.Collections.ArrayList
$data = @($global:Database)
$array.AddRange($data)
$datagridview.DataSource = $array
$global:Database = '$PSScriptRoot\data\SellerID_database.csv'
#----------------------------------------------------

	$consolecheckBox.Visible = $false
	$consolecheckBox.Location = New-Object System.Drawing.Point(540,220)
	$PricecheckBox.Visible = $false
	$PricecheckBox.Location = New-Object System.Drawing.Point(540,240)
	$ConditioncheckBox.Visible = $false
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(540,280)
	$CompatcheckBox.Visible = $false
	$CompatcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$ConditioncheckBox.Visible = $false
	$ConditioncheckBox.Location = New-Object System.Drawing.Point(540,280)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$GameRegioncheckBox.Visible = $false
	$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
	$gamenamecheckBox.Visible = $false
	$gamenamecheckBox.Location = New-Object System.Drawing.Point(540,260)
	$ratingcheckBox.Visible = $false
	$ratingcheckBox.Location = New-Object System.Drawing.Point(650,220)
	$ConsoleModelcheckBox.Visible = $false
	$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(540,260)
	$SerialNumbercheckBox.Visible = $false
	$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(540,300)
    $TitleNameCBox.Visible = $false
    $ItemNameCBox.Visible = $false
    $FormatcheckBox.Visible = $false


}

function SoldItem {
    
    try{

    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {

        $SelectedRow = $datagridview.SelectedRows.Cells[0].Value 
        $Model = $datagridview.SelectedRows.Cells[1].Value
        $ItemPrice = $datagridview.SelectedRows.Cells[2].Value 
        $SerialNumber = $datagridview.SelectedRows.Cells[5].Value 
        $Register = $global:RegStat.Text
        $Quantity = $datagridview.SelectedRows.Cells[7].Value 


        if ([int]$Quantity -eq 1) {

        $CleanCSV = Import-CSV $PSScriptRoot\data\console_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Console Name' , "$SelectedRow")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price 
        $CleanCSV[$RowIndex].Sold = "Y"

        $AppErrorLabel.Text = "Status: Updated $SelectedRow $Model to Sold!"
        #[System.Windows.MessageBox]::Show("Successfully updated Console List!")
        "[Item Sold] | Console List | $SelectedRow | $ $ItemPrice | $SerialNumber | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Console List | $SelectedRow | $ $ItemPrice | $SerialNumber | $ $Register | " | Out-File $SoldItemReport -Append

        $CleanCSV | select 'Console Name','Console Model',Price,Condition,Region,'Serial Number',Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\console_database.csv -nti
                
        PopulateConsoles
        }
        elseif ([int]$Quantity -gt 1) {

        $CleanCSV = Import-CSV $PSScriptRoot\data\console_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Console Name' , "$SelectedRow")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price 
        $CleanCSV[$RowIndex].Quantity = [int]$Quantity - 1

        $AppErrorLabel.Text = "Status: Updated $SelectedRow $Model to Sold!"
        #[System.Windows.MessageBox]::Show("Successfully updated Console List!")
        "[Item Sold] | Console List | $SelectedRow | $ $ItemPrice | $SerialNumber | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Console List | $SelectedRow | $ $ItemPrice | $SerialNumber | $ $Register | " | Out-File $SoldItemReport -Append

        $CleanCSV | select 'Console Name','Console Model',Price,Condition,Region,'Serial Number',Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\console_database.csv -nti
                
        PopulateConsoles
        }

       

    }
    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv') {

        $SelectedRow = $datagridview.SelectedRows.Cells[0].Value   
        $GameName = $datagridview.SelectedRows.Cells[1].Value
        $ItemPrice = $datagridview.SelectedRows.Cells[2].Value
        $Register = $global:RegStat.Text
        $Quantity = $datagridview.SelectedRows.Cells[7].Value
        

        if ([int]$Quantity -eq 1){
            
        $CleanCSV = Import-CSV $PSScriptRoot\data\game_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Game Name' , "$GameName")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Sold = "Y"
        $CleanCSV | select 'Console Name','Game Name',Price,Condition,Rating,Region,Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\game_database.csv -nti

        $AppErrorLabel.Text = "Status: Updated copy of $GameName for $SelectedRow to Sold!"
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | Game List | $SelectedRow | $GameName | $ $ItemPrice  | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Game List | $SelectedRow | $GameName | $ $ItemPrice  | $ $Register | " | Out-File $SoldItemReport -Append

        

        PopulateGames
     }

        elseif ([int]$Quantity -gt 1){

        $CleanCSV = Import-CSV $PSScriptRoot\data\game_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Game Name' , "$GameName")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Quantity = [int]$Quantity - 1
        $CleanCSV | select 'Console Name','Game Name',Price,Condition,Rating,Region,Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\game_database.csv -nti

        $AppErrorLabel.Text = "Status: Updated copy of $GameName for $SelectedRow to Sold!"
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | Game List | $SelectedRow | $GameName | $ $ItemPrice  | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Game List | $SelectedRow | $GameName | $ $ItemPrice  | $ $Register | " | Out-File $SoldItemReport -Append

        

        PopulateGames
    }

    



}
    elseif ($global:Database -eq '$PSScriptRoot\data\access_database.csv') {

        $SelectedRow = $datagridview.SelectedRows.Cells[0].Value  
        $ItemType = $datagridview.SelectedRows.Cells[1].Value
        $ItemPrice = $datagridview.SelectedRows.Cells[2].Value
        $Register = $global:RegStat.Text
        $Quantity = $datagridview.SelectedRows.Cells[5].Value

        if ([int]$Quantity -eq 1){
  
        $CleanCSV = Import-CSV $PSScriptRoot\data\access_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Item Type' , "$ItemType")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Sold = "Y"
        $CleanCSV | select 'Console Name','Item Type',Price,Condition,Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\access_database.csv -nti        

        $AppErrorLabel.Text = "Status: Updated $SelectedRow $ItemType to Sold!"
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | Access List | $SelectedRow | $ItemType | $ $ItemPrice  | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Access List | $SelectedRow | $ItemType | $ $ItemPrice  | $ $Register | " | Out-File $SoldItemReport -Append

        AccessoriesButton
        }

        elseif ([int]$Quantity -gt 1){

        $CleanCSV = Import-CSV $PSScriptRoot\data\access_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Item Type' , "$ItemType")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Quantity = [int]$Quantity - 1
        $CleanCSV | select 'Console Name','Item Type',Price,Condition,Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\access_database.csv -nti        

        $AppErrorLabel.Text = "Status: Updated $SelectedRow $ItemType to Sold!"
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | Access List | $SelectedRow | $ItemType | $ $ItemPrice  | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Access List | $SelectedRow | $ItemType | $ $ItemPrice  | $ $Register | " | Out-File $SoldItemReport -Append

        AccessoriesButton
        }


    } 
    elseif($global:Database -eq '$PSScriptRoot\data\bluray_database.csv'){ 

        $SelectedRow = $datagridview.SelectedRows.Cells[0].Value  
        $ItemPrice = $datagridview.SelectedRows.Cells[2].Value
        $Register = $global:RegStat.Text   
        $Quantity = $datagridview.SelectedRows.Cells[7].Value   
        
        if ([int]$Quantity -eq 1) { 
        $CleanCSV = Import-CSV $PSScriptRoot\data\bluray_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Title Name' , "$SelectedRow")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Sold = "Y"
        $CleanCSV | select 'Title Name',Condition,Price,Rating,Region,Genre,Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\bluray_database.csv -nti   

        $AppErrorLabel.Text = 'Status: Updated $SelectedRow to Sold!'
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | BluRay List | $SelectedRow | $ $ItemPrice | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | BluRay List | $SelectedRow | $ $ItemPrice | $ $Register | " | Out-File $SoldItemReport -Append

        PopulateBluRay
        }

        elseif ([int]$Quantity -gt 1) { 
        $CleanCSV = Import-CSV $PSScriptRoot\data\bluray_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Title Name' , "$SelectedRow")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Quantity = [int]$Quantity - 1
        $CleanCSV | select 'Title Name',Condition,Price,Rating,Region,Genre,Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\bluray_database.csv -nti   

        $AppErrorLabel.Text = 'Status: Updated $SelectedRow to Sold!'
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | BluRay List | $SelectedRow | $ $ItemPrice | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | BluRay List | $SelectedRow | $ $ItemPrice | $ $Register | " | Out-File $SoldItemReport -Append

        PopulateBluRay
        }


    } 
    elseif($global:Database -eq '$PSScriptRoot\data\collectable_database.csv'){

        $SelectedRow = $datagridview.SelectedRows.Cells[0].Value   
        $ItemFormat = $datagridview.SelectedRows.Cells[1].Value
        $ItemPrice = $datagridview.SelectedRows.Cells[2].Value
        $Register = $global:RegStat.Text
        $Quantity = $datagridview.SelectedRows.Cells[6].Value


        if([int]$Quantity -eq 1){
        $CleanCSV = Import-CSV $PSScriptRoot\data\collectable_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Item Name' , "$SelectedRow")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Sold = "Y"
        $CleanCSV | select "Item Name","Item Format",Price,Condition,"Product Owner",Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\collectable_database.csv -nti   

        $AppErrorLabel.Text = 'Status: Updated $SelectedRow to Sold!'
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | Collectable List | $SelectedRow | $ItemFormat | $ $ItemPrice | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Collectable List | $SelectedRow | $ItemFormat | $ $ItemPrice | $ $Register | " | Out-File $SoldItemReport -Append

        PopulateCollectables
        }
        elseif([int]$Quantity -gt 1){
        $CleanCSV = Import-CSV $PSScriptRoot\data\collectable_database.csv
        $RowIndex = [array]::IndexOf($CleanCSV.'Item Name' , "$SelectedRow")
        $global:RegStat.Text = [int]$global:RegStat.Text + [int]$CleanCSV[$RowIndex].Price
        $CleanCSV[$RowIndex].Quantity = [int]$Quantity - 1
        $CleanCSV | select "Item Name","Item Format",Price,Condition,"Product Owner",Included,Quantity,UPC,Sold,Sold-Date | export-csv $PSScriptRoot\data\collectable_database.csv -nti   

        $AppErrorLabel.Text = 'Status: Updated $SelectedRow to Sold!'
        #[System.Windows.MessageBox]::Show("Updated $SelectedRow to Sold!")
        "[Item Sold] | Collectable List | $SelectedRow | $ItemFormat | $ $ItemPrice | $ $Register | " | Out-File $DailyActionReport -Append
        "[Item Sold] | Collectable List | $SelectedRow | $ItemFormat | $ $ItemPrice | $ $Register | " | Out-File $SoldItemReport -Append

        PopulateCollectables
        }



    } 
    elseif($global:Database -eq '$PSScriptRoot\data\SellerID_database.csv'){

        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\SellerID_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated Seller ID List!'
        #[System.Windows.MessageBox]::Show("Successfully updated Seller ID List!")
        "[LIST UPDATED] | Updated Seller ID List |" | Out-File $DailyActionReport -Append
        SellerIDList   
    }

    else {
    $AppErrorLabel.Text = 'Error! : No database(s) found!'
    #[System.Windows.MessageBox]::Show('Error! : No database(s) found!') 
    "[Error] | Attempted to save with no databases in \data\ |" | Out-File $DailyActionReport -Append
    }
    $global:RecentUpdate = $false
    }
    catch{$AppErrorLabel.Text = "Error: Please select the entire row before marking the item sold!"}


}

function SaveList {
    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {


        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\console_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated Console List!'
        #[System.Windows.MessageBox]::Show("Successfully updated Console List!")
        "[LIST UPDATED] | Updated Console List |" | Out-File $DailyActionReport -Append

        PopulateConsoles
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv') {

        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\game_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated Game List!'
        #[System.Windows.MessageBox]::Show("Successfully updated Game List!")
        "[LIST UPDATED] | Updated Game List |" | Out-File $DailyActionReport -Append

        PopulateGames
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\access_database.csv') {

        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\access_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated Accessories List!'
        #[System.Windows.MessageBox]::Show("Successfully updated Accessories List!")
        "[LIST UPDATED] | Updated Accessories List |" | Out-File $DailyActionReport -Append

        AccessoriesButton

    } 
    elseif($global:Database -eq '$PSScriptRoot\data\bluray_database.csv'){ 

        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\bluray_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated BluRay List!'
        #[System.Windows.MessageBox]::Show("Successfully updated BluRay List!")
        "[LIST UPDATED] | Updated BluRay List |" | Out-File $DailyActionReport -Append

        PopulateBluRay

    } 
    elseif($global:Database -eq '$PSScriptRoot\data\collectable_database.csv'){

        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\collectable_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated Collectable List!'
        #[System.Windows.MessageBox]::Show("Successfully updated Collectables List!")
        "[LIST UPDATED] | Updated Collectables List |" | Out-File $DailyActionReport -Append

        PopulateCollectables
    } 
    elseif($global:Database -eq '$PSScriptRoot\data\SellerID_database.csv'){

        $datagridview.Rows | select -expand DataBoundItem | export-csv $PSScriptRoot\data\SellerID_database.csv
        $AppErrorLabel.Text = 'Status: Successfully updated Seller ID List!'
        #[System.Windows.MessageBox]::Show("Successfully updated Seller ID List!")
        "[LIST UPDATED] | Updated Seller ID List |" | Out-File $DailyActionReport -Append
        SellerIDList   
    }

    else {
    $AppErrorLabel.Text = 'Error! : No database(s) found!'
    #[System.Windows.MessageBox]::Show('Error! : No database(s) found!') 
    "[Error] | Attempted to save with no databases in \data\ |" | Out-File $DailyActionReport -Append
    }
    $global:RecentUpdate = $false

}

function SoldConsoles {

  
    $global:Database = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.Sold -eq "Y"}
    "[ITEM SOLD] | $global:Database.'Console Name'| $global:Database.Price | $global:Database.'Serial Number' |" | Out-File $SoldItemReport -Append
  

}

function SoldGames {
    $GameDatabase = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.Sold -eq "Y"}

    $array = New-Object System.Collections.ArrayList
    $data = @($GameDatabase)
    $array.AddRange($data)
    $datagridview.DataSource = $array

}

function SoldAccessory {
    $AccessDatabase = Import-CSV $PSScriptRoot\data\access_database.csv | where {$_.Sold -eq "Y"}

    $array = New-Object System.Collections.ArrayList
    $data = @($AccessDatabase)
    $array.AddRange($data)
    $datagridview.DataSource = $array

}

function DatabaseBackup {
    
    $DateTime = Get-Date -Format "dddd MM/dd/yyy"

    Copy-Item $PSScriptRoot\data\access_database.csv -Destination $PSScriptRoot\backup\databases
    Copy-Item $PSScriptRoot\data\console_database.csv -Destination $PSScriptRoot\backup\databases
    Copy-Item $PSScriptRoot\data\game_database.csv -Destination $PSScriptRoot\backup\databases
    Copy-Item $PSScriptRoot\data\bluray_database.csv -Destination $PSScriptRoot\backup\databases
    Copy-Item $PSScriptRoot\data\collectable_database.csv -Destination $PSScriptRoot\backup\databases
    Copy-Item $PSScriptRoot\data\SellerID_database.csv -Destination $PSScriptRoot\backup\databases

    $AppErrorLabel.Text = "Successfully backed databases up to" + "`n" + "$PSScriptRoot\backup\databases"
    $AppErrorLabel.Size = New-Object System.Drawing.Size(700,20)
    #[System.Windows.MessageBox]::Show("Successfully backed databases up to" + "`n" + "$PSScriptRoot\backup\databases")
    "[Database Backup] | Backed Databases Up To $PSScriptRoot\backup\databases|" | Out-File $DailyActionReport -Append
}

function RestoreBackup {
    
    $DateTime = Get-Date -Format "dddd MM/dd/yyy"

    Copy-Item $PSScriptRoot\backup\databases\access_database.csv -Destination $PSScriptRoot\data\access_database.csv
    Copy-Item $PSScriptRoot\backup\databases\console_database.csv -Destination $PSScriptRoot\data\console_database.csv
    Copy-Item $PSScriptRoot\backup\databases\game_database.csv -Destination $PSScriptRoot\data\game_database.csv
    Copy-Item $PSScriptRoot\backup\databases\bluray_database.csv -Destination $PSScriptRoot\data\bluray_database.csv
    Copy-Item $PSScriptRoot\backup\databases\collectable_database.csv -Destination $PSScriptRoot\data\collectable_database.csv
    Copy-Item $PSScriptRoot\backup\databases\SellerID_database.csv -Destination $PSScriptRoot\data\SellerID_database.csv

    $AppErrorLabel.Text = "Successfully restored databases to" + "`n" + "$PSScriptRoot\data\"
    #[System.Windows.MessageBox]::Show("Successfully restored databases to" + "`n" + "$PSScriptRoot\data\")
    "[Database Restored] | Restored Databases To $PSScriptRoot\data\|" | Out-File $DailyActionReport -Append
}

function NewDB {
"Console Name,Console Model,Price,Condition,Region,Serial Number,Included,Quantity,UPC,Sold,Sold-Date" | Out-File $PSScriptRoot\data\console_database.csv -Append -Encoding utf8
",,,,,,,,,," | Out-File $PSScriptRoot\data\console_database.csv -Append -Encoding utf8
",,,,,,,,,," | Out-File $PSScriptRoot\data\console_database.csv -Append -Encoding utf8


"Console Name,Game Name,Price,Condition,Rating,Region,Included,Quantity,UPC,Sold,Sold-Date" | Out-File $PSScriptRoot\data\game_database.csv -Append -Encoding utf8
",,,,,,,,,,," | Out-File $PSScriptRoot\data\game_database.csv -Append -Encoding utf8
",,,,,,,,,,," | Out-File $PSScriptRoot\data\game_database.csv -Append -Encoding utf8


"Title Name,Condition,Price,Rating,Region,Genre,Format,Quantity,UPC,Sold,Sold-Date" | Out-File $PSScriptRoot\data\bluray_database.csv -Append -Encoding utf8
",,,,,,,,,,," | Out-File $PSScriptRoot\data\bluray_database.csv -Append -Encoding utf8
",,,,,,,,,,," | Out-File $PSScriptRoot\data\bluray_database.csv -Append -Encoding utf8


"Item Name,Item Format,Price,Condition,Product Owner,Included,Quantity,UPC,Sold,Sold-Date" | Out-File $PSScriptRoot\data\collectable_database.csv -Append -Encoding utf8
",,,,,,,,,," | Out-File $PSScriptRoot\data\collectable_database.csv -Append -Encoding utf8
",,,,,,,,,," | Out-File $PSScriptRoot\data\collectable_database.csv -Append -Encoding utf8


"Console Name,Item Type,Price,Condition,Included,Quantity,UPC,Sold,Sold-Date" | Out-File $PSScriptRoot\data\access_database.csv -Append -Encoding utf8
",,,,,,,," | Out-File $PSScriptRoot\data\access_database.csv -Append -Encoding utf8
",,,,,,,," | Out-File $PSScriptRoot\data\access_database.csv -Append -Encoding utf8


"Full Name,UN######,D.O.B,Purchase Total,Purchase Date,Purchase Time,Description,UPC" | Out-File $PSScriptRoot\data\SellerID_database.csv -Append -Encoding utf8
",,,,,,,," | Out-File $PSScriptRoot\data\SellerID_database.csv -Append -Encoding utf8
",,,,,,,," | Out-File $PSScriptRoot\data\SellerID_database.csv -Append -Encoding utf8
}

function Search {

 if ($consolecheckBox.Checked -eq $true) {
    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.'Console Name' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array
        }
    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv'){
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.'Console Name' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array             
        }
    elseif ($global:Database -eq '$PSScriptRoot\data\access_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\access_database.csv | where {$_.'Console Name' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array        
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}
}

 elseif ($gamenamecheckBox.Checked -eq $true){
     if ($global:Database -eq '$PSScriptRoot\data\game_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.'Game Name' -like $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}  
}

 elseif ($ratingcheckBox.Checked -eq $true) {
      if ($global:Database -eq '$PSScriptRoot\data\game_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.Rating -like $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array
        }  
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}
 }

 elseif ($PricecheckBox.Checked -eq $true){
    
    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.'Price' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array    
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv'){
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.'Price' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array      
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\access_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\access_database.csv | where {$_.'Price' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array       
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\collectable_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\collectable_database.csv | where {$_.'Price' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array      
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\bluray_database.csv'){
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\bluray_database.csv | where {$_.'Price' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array        
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}
 }

 elseif ($GameRegioncheckBox.Checked -eq $true){

    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.'Region' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array      
    }
    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv'){
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.'Region' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array     
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}
 
 }   

 elseif ($ConsoleModelcheckBox.Checked -eq $true) {

    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.'Console Model' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array   
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}
 
 }

 elseif ($CompatcheckBox.Checked -eq $true) {

    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {}
    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv'){}
    elseif ($global:Database -eq '$PSScriptRoot\data\access_database.csv') {}
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"} 
 
 }

 elseif ($ConditioncheckBox.Checked -eq $true) {

    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.'Condition' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array     
    }

    elseif ($global:Database -eq '$PSScriptRoot\data\game_database.csv'){
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\game_database.csv | where {$_.'Condition' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array      
    }

    elseif ($global:Database -eq '$PSScriptRoot\data\access_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\access_database.csv | where {$_.'Condition' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array      
    }

    elseif ($global:Database -eq '$PSScriptRoot\data\collectable_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\collectable_database.csv | where {$_.'Condition' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array     
    }

    elseif ($global:Database -eq '$PSScriptRoot\data\bluray_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\bluray_database.csv | where {$_.'Condition' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array        
    }

    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}

 }

 elseif ($SerialNumbercheckBox.Checked -eq $true) {

    if ($global:Database -eq '$PSScriptRoot\data\console_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\console_database.csv | where {$_.'Serial Number' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array   
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"} 
 
 }

 elseif ($FormatcheckBox.Checked -eq $true) {
     if ($global:Database -eq '$PSScriptRoot\data\bluray_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\bluray_database.csv | where {$_.'Format' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array   
    }   
    elseif ($global:Database -eq '$PSScriptRoot\data\collectable_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\collectable_database.csv | where {$_.'Item Format' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array   
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"} 
 }

 elseif ($ItemNameCBox.Checked -eq $true) {
       if ($global:Database -eq '$PSScriptRoot\data\collectable_database.csv') {
        $search = $SearchBox.Text 
        $file = Import-CSV $PSScriptRoot\data\collectable_database.csv | where {$_.'Item Name' -eq $search}
        $array = New-Object System.Collections.ArrayList
        $data = @($file)
        $array.AddRange($data)
        $datagridview.DataSource = $array   
    }
    else{$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}
 }

 else {$AppErrorLabel.Text = "Error: Please Select a Checkbox First"}

}

function Options {

Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
#------------Main Window-----------------------------
$form = New-Object System.Windows.Forms.Form
$form.Text = 'Inventory Manager'
$form.Size = New-Object System.Drawing.Size(200,250)
$form.StartPosition = 'CenterScreen'
$form.FormBorderStyle = 'Fixed3D'

#----------------------------------------------------
#-------------------Backup DB Item Button-----------------------------
$BackupDB = New-Object System.Windows.Forms.Button
$BackupDB.Location = New-Object System.Drawing.Point(55,40)
$BackupDB.Size = New-Object System.Drawing.Size(95,40)
$BackupDB.Text = 'Backup Databases'
$form.Controls.Add($BackupDB)

$BackupDB.Add_Click({
    DatabaseBackup
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
})
#-----------------------------------------------------------------
#-------------------Restore DB Item Button-----------------------------
$RestoreDB = New-Object System.Windows.Forms.Button
$RestoreDB.Location = New-Object System.Drawing.Point(55,85)
$RestoreDB.Size = New-Object System.Drawing.Size(95,40)
$RestoreDB.Text = 'Restore Databases'
$form.Controls.Add($RestoreDB)

$RestoreDB.Add_Click({
    RestoreBackup
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
})
#-----------------------------------------------------------------
#-------------------New DB Item Button-----------------------------
$NewDB = New-Object System.Windows.Forms.Button
$NewDB.Location = New-Object System.Drawing.Point(55,130)
$NewDB.Size = New-Object System.Drawing.Size(95,40)
$NewDB.Text = 'New Databases'
$form.Controls.Add($NewDB)

$NewDB.Add_Click({
    NewDB
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
})
#-----------------------------------------------------------------

$form.ShowDialog()
}

function StartDay {
    
    $global:ShopStat.Text = 'OPEN'

    "[STORE OPEN] | Store Opened at $GetDate |" | Out-File $DailyActionReport -Append
    "[STORE OPEN] | Store Opened at $GetDate | " | Out-File $SoldItemReport -Append

    $form = New-Object System.Windows.Forms.Form
    $form.Text = 'Inventory Manager'
    $form.Size = New-Object System.Drawing.Size(300,200)
    $form.StartPosition = 'CenterScreen'
    $form.FormBorderStyle = 'Fixed3D'

    $Label = New-Object System.Windows.Forms.Label
    $Label.Location = New-Object System.Drawing.Point(50,40)
    $Label.Size = New-Object System.Drawing.Size(200,20)
    $Label.Text = 'Please enter the current register count:'
    $form.Controls.Add($Label)

    $MoneyBox = New-Object System.Windows.Forms.TextBox
    $MoneyBox.Location = New-Object System.Drawing.Point(100,60)
    $MoneyBox.Size = New-Object System.Drawing.Size(100,20)
    $form.Controls.Add($MoneyBox)

    $MoneyLabel = New-Object System.Windows.Forms.Label
    $MoneyLabel.Location = New-Object System.Drawing.Point(90,65)
    $MoneyLabel.Size = New-Object System.Drawing.Size(10,40)
    $MoneyLabel.Text = '$'
    $form.Controls.Add($MoneyLabel)

    $OKButton = New-Object System.Windows.Forms.Button
    $OKButton.Location = New-Object System.Drawing.Point(120,100)
    $OKButton.Size = New-Object System.Drawing.Size(50,20)
    $OKButton.Text = "OK"
    $form.Controls.Add($OKButton)

    $OKButton.Add_Click({
        $form.Close()
        $global:RegStat.Text = $MoneyBox.Text
        $global:RegisterCount = $global:RegStat.Text | Out-String
        "[ACTION] | Register Count | $global:RegisterCount" | Out-File $DailyActionReport -Append

    })

    $form.ShowDialog()
}

function NewSale {

    $form = New-Object System.Windows.Forms.Form
    $form.Text = 'Inventory Manager'
    $form.Size = New-Object System.Drawing.Size(300,200)
    $form.StartPosition = 'CenterScreen'
    $form.FormBorderStyle = 'Fixed3D'

    $Label = New-Object System.Windows.Forms.Label
    $Label.Location = New-Object System.Drawing.Point(50,40)
    $Label.Size = New-Object System.Drawing.Size(200,20)
    $Label.Text = 'Please enter sale amount:'
    $form.Controls.Add($Label)

    $MoneyBox = New-Object System.Windows.Forms.TextBox
    $MoneyBox.Location = New-Object System.Drawing.Point(100,60)
    $MoneyBox.Size = New-Object System.Drawing.Size(100,20)
    $form.Controls.Add($MoneyBox)

    $MoneyLabel = New-Object System.Windows.Forms.Label
    $MoneyLabel.Location = New-Object System.Drawing.Point(90,65)
    $MoneyLabel.Size = New-Object System.Drawing.Size(10,40)
    $MoneyLabel.Text = '$'
    $form.Controls.Add($MoneyLabel)

    $OKButton = New-Object System.Windows.Forms.Button
    $OKButton.Location = New-Object System.Drawing.Point(120,100)
    $OKButton.Size = New-Object System.Drawing.Size(50,20)
    $OKButton.Text = "OK"
    $form.Controls.Add($OKButton)

    $OKButton.Add_Click({
        $form.Close()
        $global:RegStat.Text = [int]$MoneyBox.Text + [int]$global:RegStat.Text
        $global:RegisterCount = $global:RegStat.Text | Out-String
        "[ACTION] | Register Count | $global:RegisterCount" | Out-File $DailyActionReport -Append

    })

    $form.ShowDialog()

}

function NewPurchase {

    $form = New-Object System.Windows.Forms.Form
    $form.Text = 'Inventory Manager'
    $form.Size = New-Object System.Drawing.Size(300,200)
    $form.StartPosition = 'CenterScreen'
    $form.FormBorderStyle = 'Fixed3D'

    $Label = New-Object System.Windows.Forms.Label
    $Label.Location = New-Object System.Drawing.Point(50,40)
    $Label.Size = New-Object System.Drawing.Size(200,20)
    $Label.Text = 'Please enter purchase amount:'
    $form.Controls.Add($Label)

    $MoneyBox = New-Object System.Windows.Forms.TextBox
    $MoneyBox.Location = New-Object System.Drawing.Point(100,60)
    $MoneyBox.Size = New-Object System.Drawing.Size(100,20)
    $form.Controls.Add($MoneyBox)

    $MoneyLabel = New-Object System.Windows.Forms.Label
    $MoneyLabel.Location = New-Object System.Drawing.Point(90,65)
    $MoneyLabel.Size = New-Object System.Drawing.Size(10,40)
    $MoneyLabel.Text = '$'
    $form.Controls.Add($MoneyLabel)

    $OKButton = New-Object System.Windows.Forms.Button
    $OKButton.Location = New-Object System.Drawing.Point(120,100)
    $OKButton.Size = New-Object System.Drawing.Size(50,20)
    $OKButton.Text = "OK"
    $form.Controls.Add($OKButton)

    $OKButton.Add_Click({
        $form.Close()
        $global:RegStat.Text = [int]$global:RegStat.Text - [int]$MoneyBox.Text
        $global:RegisterCount = $global:RegStat.Text | Out-String
        "[ACTION] | Register Count | $global:RegisterCount" | Out-File $DailyActionReport -Append

    })

    $form.ShowDialog()

}

#-----------------------------------------------------------------------

#------------Main Window-----------------------------
$form = New-Object System.Windows.Forms.Form
$form.Text = 'Inventory Manager'
$form.Size = New-Object System.Drawing.Size(810,710)
$form.StartPosition = 'CenterScreen'
$form.FormBorderStyle = 'Fixed3D'
#----------------------------------------------------

# Logging Data File Creation
$GetDate = Get-Date -Format "dddd MM/dd/yyy HH:mm"
$DailyActionReport = "$PSScriptRoot\data\logs\DailyActionReport.txt"
$SoldItemReport = "$PSScriptRoot\data\logs\SoldItemReport.txt"
"[ACTION] | Application Started at $GetDate |" | Out-File $DailyActionReport -Append

# global vars
$global:RecentUpdate = $false

#---------------------------------------------------
#-----------------Searching Options------------------

$SearchLabel = New-Object System.Windows.Forms.Label
$SearchLabel.Location = New-Object System.Drawing.Point(545,175)
$SearchLabel.Size = New-Object System.Drawing.Size(50,20)
$SearchLabel.Text = 'Search:'
$form.Controls.Add($SearchLabel)

# Search Box
$SearchBox =  New-Object System.Windows.Forms.TextBox
$SearchBox.Location = New-Object System.Drawing.Point(545,195)
$SearchBox.Size = New-Object System.Drawing.Size(190,40)
$form.Controls.Add($SearchBox)

$SearchBox.Add_KeyDown({
    if ($_.KeyCode -eq "Enter") {
            Search
            $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
            "[ACTION] | User initiated a search |" | Out-File $DailyActionReport -Append
            $AppErrorLabel.Text = ''
    }

})

$SearchItem = New-Object System.Windows.Forms.Button
$SearchItem.Location = New-Object System.Drawing.Point(740,195)
$SearchItem.Size = New-Object System.Drawing.Size(40,20)
$SearchItem.Text = 'Go'
$form.Controls.Add($SearchItem)

$SearchItem.Add_Click({
    Search
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    "[ACTION] | User initiated a search |" | Out-File $DailyActionReport -Append
    $AppErrorLabel.Text = ''
})

#----------------------------------------------------
#---------------------- Application Status Header -------------------------
$AppErrorLabel = New-Object System.Windows.Forms.Label
$AppErrorLabel.Location = New-Object System.Drawing.Point(10,310)
$AppErrorLabel.Size = New-Object System.Drawing.Size(450,20)
$AppErrorLabel.Text = ''
$form.Controls.Add($AppErrorLabel)
#----------------------------------------------------
#------------------Data Grid for listing----------------------------
$datagridview = New-Object System.Windows.Forms.DataGridView
$datagridview.Location = New-Object System.Drawing.Point(10,330)
$datagridview.Size = New-Object System.Drawing.Size(770,330)
$datagridview.ColumnHeadersHeight = 40
$datagridview.AllowUserToResizeColumns = $false
$datagridview.AllowUserToOrderColumns = $true
$datagridview.AutoSizeColumnsMode = 'DisplayedCells'
$datagridview.AutoSizeRowsMode = 'DisplayedCells'
$form.Controls.Add($datagridview)
#------------------------------------------------------------------
#---------------------- Application Header -------------------------
$AppLabel = New-Object System.Windows.Forms.Label
$AppLabel.Location = New-Object System.Drawing.Point(20,30)
$AppLabel.Size = New-Object System.Drawing.Size(250,20)
$AppLabel.Text = 'Inventory Manager'
$form.Controls.Add($AppLabel)
#----------------------------------------------------
#---------------------- DateTime Header -------------------------
$DateTimeText = New-Object System.Windows.Forms.Label
$DateTimeText.Location = New-Object System.Drawing.Point(270,30)
$DateTimeText.Size = New-Object System.Drawing.Size(250,20)
$DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
$form.Controls.Add($DateTimeText)
#----------------------------------------------------
#----------------------Top Line-------------------------
$linelabel = New-Object System.Windows.Forms.Label
$linelabel.Location = New-Object System.Drawing.Point(15,50)
$linelabel.Size = New-Object System.Drawing.Size(500,20)
$linelabel.Text = '---------------------------------------------------------------------------------------------------------------------------'
$form.Controls.Add($linelabel)
#----------------------------------------------------
#---------------------- Shop Status Header -------------------------
$ShopStatLabel = New-Object System.Windows.Forms.Label
$ShopStatLabel.Location = New-Object System.Drawing.Point(550,70)
$ShopStatLabel.Size = New-Object System.Drawing.Size(80,20)
$ShopStatLabel.Text = 'Shop Status:'
$form.Controls.Add($ShopStatLabel)
#----------------------------------------------------
#---------------------- Shop Status Text -------------------------
$global:ShopStat = New-Object System.Windows.Forms.Label
$global:ShopStat.Location = New-Object System.Drawing.Point(630,70)
$global:ShopStat.Size = New-Object System.Drawing.Size(100,20)
$global:ShopStat.Text = 'Just Arrived'
$form.Controls.Add($global:ShopStat)
#----------------------------------------------------
#---------------------- Register Status Header -------------------------
$RegStatLabel = New-Object System.Windows.Forms.Label
$RegStatLabel.Location = New-Object System.Drawing.Point(550,90)
$RegStatLabel.Size = New-Object System.Drawing.Size(90,20)
$RegStatLabel.Text = 'Register Count:'
$form.Controls.Add($RegStatLabel)
#----------------------------------------------------
# Dollar symbol 1
$MoneyLabel = New-Object System.Windows.Forms.Label
$MoneyLabel.Location = New-Object System.Drawing.Point(640,90)
$MoneyLabel.Size = New-Object System.Drawing.Size(10,20)
$MoneyLabel.Text = '$'
$form.Controls.Add($MoneyLabel)
#---------------------- Register Status Text -------------------------
$global:RegStat = New-Object System.Windows.Forms.Label
$global:RegStat.Location = New-Object System.Drawing.Point(650,90)
$global:RegStat.Size = New-Object System.Drawing.Size(100,20)
$global:RegStat.Text = '000.00'
$form.Controls.Add($global:RegStat)
#----------------------------------------------------

#---------------------- Net Profit Status Header -------------------------
$TProfitLabel = New-Object System.Windows.Forms.Label
$TProfitLabel.Location = New-Object System.Drawing.Point(550,110)
$TProfitLabel.Size = New-Object System.Drawing.Size(80,20)
$TProfitLabel.Text = 'Todays Profit:'
#$form.Controls.Add($TProfitLabel)
#----------------------------------------------------
# Dollar symbol 2
$Money2Label = New-Object System.Windows.Forms.Label
$Money2Label.Location = New-Object System.Drawing.Point(640,110)
$Money2Label.Size = New-Object System.Drawing.Size(10,20)
$Money2Label.Text = '$'
#$form.Controls.Add($Money2Label)
#---------------------- Net Profit Text -------------------------
$global:TProfitStat = New-Object System.Windows.Forms.Label
$global:TProfitStat.Location = New-Object System.Drawing.Point(650,110)
$global:TProfitStat.Size = New-Object System.Drawing.Size(100,20)
$global:TProfitStat.Text = '000.00'
#$form.Controls.Add($global:TProfitStat)
#----------------------------------------------------

#-------------------Start Day Button-----------------------------
$StartDay = New-Object System.Windows.Forms.Button
$StartDay.Location = New-Object System.Drawing.Point(205,70)
$StartDay.Size = New-Object System.Drawing.Size(90,30)
$StartDay.Text = 'Start Day'
$form.Controls.Add($StartDay)

$StartDay.Add_Click({
    StartDay
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#--------------------------------------------------------------
#-------------------End of Day Button-----------------------------
$EndDay = New-Object System.Windows.Forms.Button
$EndDay.Location = New-Object System.Drawing.Point(205,110)
$EndDay.Size = New-Object System.Drawing.Size(90,30)
$EndDay.Text = 'End Day'
$form.Controls.Add($EndDay)

$EndDay.Add_Click({
   $global:ShopStat.Text = 'CLOSED' 
   $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
   "[STORE CLOSED] | Store Closed at $GetDate |" | Out-File $DailyActionReport -Append
   "[ACTION] | Register Count | $global:RegisterCount" | Out-File $DailyActionReport -Append
   "[STORE OPEN] | Store Closed at $GetDate | " | Out-File $SoldItemReport -Append
   $AppErrorLabel.Text = ''
})
#--------------------------------------------------------------

#-------------------New Sale Button-----------------------------
$NewSale = New-Object System.Windows.Forms.Button
$NewSale.Location = New-Object System.Drawing.Point(300,70)
$NewSale.Size = New-Object System.Drawing.Size(90,30)
$NewSale.Text = 'Sale+'
#$form.Controls.Add($NewSale)

$NewSale.Add_Click({
    NewSale
    $AppErrorLabel.Text = ''
})

#-----------------------------------------------------------------
#-------------------New Purchase Button-----------------------------
$NewPurchase = New-Object System.Windows.Forms.Button
$NewPurchase.Location = New-Object System.Drawing.Point(300,110)
$NewPurchase.Size = New-Object System.Drawing.Size(90,30)
$NewPurchase.Text = 'New Purchase'
#$form.Controls.Add($NewPurchase)

$NewPurchase.Add_Click({
    NewPurchase
    $AppErrorLabel.Text = ''
})
#-----------------------------------------------------------------

#-------------------Console List Button-----------------------------
$CListButton = New-Object System.Windows.Forms.Button
$CListButton.Location = New-Object System.Drawing.Point(15,190)
$CListButton.Size = New-Object System.Drawing.Size(90,30)
$CListButton.Text = 'Consoles'
$form.Controls.Add($CListButton)

$CListButton.Add_Click({
    PopulateConsoles
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#---------------------------------------------------------------
#-------------------Blu Ray List Button-----------------------------
$BRayList = New-Object System.Windows.Forms.Button
$BRayList.Location = New-Object System.Drawing.Point(15,110)
$BRayList.Size = New-Object System.Drawing.Size(90,30)
$BRayList.Text = 'BluRay / DVD'
$form.Controls.Add($BRayList)

$BRayList.Add_Click({
    PopulateBluRay
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#---------------------------------------------------------------
#-------------------Seller ID List Button-----------------------------
$SellerIDList = New-Object System.Windows.Forms.Button
$SellerIDList.Location = New-Object System.Drawing.Point(15,270)
$SellerIDList.Size = New-Object System.Drawing.Size(90,30)
$SellerIDList.Text = 'Seller IDs'
$form.Controls.Add($SellerIDList)

$SellerIDList.Add_Click({
    SellerIDList
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#---------------------------------------------------------------
#-------------------Game List Button-----------------------------
$GListButton = New-Object System.Windows.Forms.Button
$GListButton.Location = New-Object System.Drawing.Point(15,230)
$GListButton.Size = New-Object System.Drawing.Size(90,30)
$GListButton.Text = 'Games'
$form.Controls.Add($GListButton)

$GListButton.Add_Click({
    PopulateGames
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#---------------------------------------------------------------
#-------------------Collectables List Button-----------------------------
$Collectables = New-Object System.Windows.Forms.Button
$Collectables.Location = New-Object System.Drawing.Point(15,150)
$Collectables.Size = New-Object System.Drawing.Size(90,30)
$Collectables.Text = 'Collectables'
$form.Controls.Add($Collectables)

$Collectables.Add_Click({
    PopulateCollectables
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#---------------------------------------------------------------
#-------------------Accessories List Button-----------------------------
$AccessoriesButton = New-Object System.Windows.Forms.Button
$AccessoriesButton.Location = New-Object System.Drawing.Point(15,70)
$AccessoriesButton.Size = New-Object System.Drawing.Size(90,30)
$AccessoriesButton.Text = 'Accessories'
$form.Controls.Add($AccessoriesButton)

$AccessoriesButton.Add_Click({
    AccessoriesButton
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#-----------------------------------------------------------------
#-------------------New Item Button-----------------------------
$NewCItem = New-Object System.Windows.Forms.Button
$NewCItem.Location = New-Object System.Drawing.Point(110,70)
$NewCItem.Size = New-Object System.Drawing.Size(90,30)
$NewCItem.Text = 'Add New Item'
$form.Controls.Add($NewCItem)

$NewCItem.Add_Click({
    NewCItem
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#--------------------------------------------------------------
#-------------------Sold Item Button-----------------------------
$SoldItem = New-Object System.Windows.Forms.Button
$SoldItem.Location = New-Object System.Drawing.Point(110,110)
$SoldItem.Size = New-Object System.Drawing.Size(90,30)
$SoldItem.Text = 'Mark Sold'
$form.Controls.Add($SoldItem)

$SoldItem.Add_Click({
    SoldItem
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
})
#-----------------------------------------------------------------
#-------------------Save List Button-----------------------------
$SaveList = New-Object System.Windows.Forms.Button
$SaveList.Location = New-Object System.Drawing.Point(110,150)
$SaveList.Size = New-Object System.Drawing.Size(90,30)
$SaveList.Text = 'Update List'
$form.Controls.Add($SaveList)

$SaveList.Add_Click({
    SaveList
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
})
#-----------------------------------------------------------------
#-------------------Options Button-----------------------------
$Options = New-Object System.Windows.Forms.Button
$Options.Location = New-Object System.Drawing.Point(205,150)
$Options.Size = New-Object System.Drawing.Size(90,30)
$Options.Text = 'Options'
$form.Controls.Add($Options)

$Options.Add_Click({
    Options
    $DateTimeText.Text = Get-Date -Format "dddd MM/dd/yyy HH:mm"
    $AppErrorLabel.Text = ''
})
#-----------------------------------------------------------------

# Checkboxes for search filters------------------------------------

$ItemNameCBox = New-Object System.Windows.Forms.CheckBox
$ItemNameCBox.Location = New-Object System.Drawing.Point(550,220)
$ItemNameCBox.Size = New-Object System.Drawing.Size(90,20)
$ItemNameCBox.Text = "Item Name"
$ItemNameCBox.Visible = $false
$form.Controls.Add($ItemNameCBox)


$TitleNameCBox = New-Object System.Windows.Forms.CheckBox
$TitleNameCBox.Location = New-Object System.Drawing.Point(550,220)
$TitleNameCBox.Size = New-Object System.Drawing.Size(90,20)
$TitleNameCBox.Text = "Title Name"
$TitleNameCBox.Visible = $false
$form.Controls.Add($TitleNameCBox)


$accessoriesCBox = New-Object System.Windows.Forms.CheckBox
$accessoriesCBox.Location = New-Object System.Drawing.Point(460,220)
$accessoriesCBox.Size = New-Object System.Drawing.Size(90,20)
$accessoriesCBox.Text = "Accessories"
$accessoriesCBox.Visible = $false
$form.Controls.Add($accessoriesCBox)

$GamesCBox = New-Object System.Windows.Forms.CheckBox
$GamesCBox.Location = New-Object System.Drawing.Point(460,240)
$GamesCBox.Size = New-Object System.Drawing.Size(90,20)
$GamesCBox.Text = "Games"
$GamesCBox.Visible = $false
$form.Controls.Add($GamesCBox)

$BRayCBox = New-Object System.Windows.Forms.CheckBox
$BRayCBox.Location = New-Object System.Drawing.Point(460,260)
$BRayCBox.Size = New-Object System.Drawing.Size(90,20)
$BRayCBox.Text = "Blu Ray"
$BRayCBox.Visible = $false
$form.Controls.Add($BRayCBox)

$ConsolesCBox = New-Object System.Windows.Forms.CheckBox
$ConsolesCBox.Location = New-Object System.Drawing.Point(460,280)
$ConsolesCBox.Size = New-Object System.Drawing.Size(90,20)
$ConsolesCBox.Text = "Consoles"
$ConsolesCBox.Visible = $false
$form.Controls.Add($ConsolesCBox)

$CollectCBox = New-Object System.Windows.Forms.CheckBox
$CollectCBox.Location = New-Object System.Drawing.Point(460,300)
$CollectCBox.Size = New-Object System.Drawing.Size(90,20)
$CollectCBox.Text = "Collectables"
$CollectCBox.Visible = $false
$form.Controls.Add($CollectCBox)

# Sub List Items
$consolecheckBox = New-Object System.Windows.Forms.CheckBox
$consolecheckBox.Location = New-Object System.Drawing.Point(540,220)
$consolecheckBox.Size = New-Object System.Drawing.Size(100,20)
$consolecheckBox.Text = "Console Name"
$consolecheckBox.Visible = $false
$form.Controls.Add($consolecheckBox)

$ratingcheckBox = New-Object System.Windows.Forms.CheckBox
$ratingcheckBox.Location = New-Object System.Drawing.Point(650,220)
$ratingcheckBox.Size = New-Object System.Drawing.Size(100,20)
$ratingcheckBox.Text = "Game Rating"
$ratingcheckBox.Visible = $false
$form.Controls.Add($ratingcheckBox)


$gamenamecheckBox = New-Object System.Windows.Forms.CheckBox
$gamenamecheckBox.Location = New-Object System.Drawing.Point(540,260)
$gamenamecheckBox.Size = New-Object System.Drawing.Size(100,20)
$gamenamecheckBox.Text = "Game Name"
$gamenamecheckBox.Visible = $false
$form.Controls.Add($gamenamecheckBox)

$PricecheckBox = New-Object System.Windows.Forms.CheckBox
$PricecheckBox.Location = New-Object System.Drawing.Point(540,240)
$PricecheckBox.Size = New-Object System.Drawing.Size(100,20)
$PricecheckBox.Text = "Item Price"
$PricecheckBox.Visible = $false
$form.Controls.Add($PricecheckBox)
#
$GameRegioncheckBox = New-Object System.Windows.Forms.CheckBox
$GameRegioncheckBox.Location = New-Object System.Drawing.Point(540,300)
$GameRegioncheckBox.Size = New-Object System.Drawing.Size(100,20)
$GameRegioncheckBox.Text = "Game Region"
$GameRegioncheckBox.Visible = $false
$form.Controls.Add($GameRegioncheckBox)


$ConsoleModelcheckBox = New-Object System.Windows.Forms.CheckBox
$ConsoleModelcheckBox.Location = New-Object System.Drawing.Point(540,260)
$ConsoleModelcheckBox.Size = New-Object System.Drawing.Size(100,20)
$ConsoleModelcheckBox.Text = "Console Model"
$ConsoleModelcheckBox.Visible = $false
$form.Controls.Add($ConsoleModelcheckBox)

$CompatcheckBox = New-Object System.Windows.Forms.CheckBox
$CompatcheckBox.Location = New-Object System.Drawing.Point(650,240)
$CompatcheckBox.Size = New-Object System.Drawing.Size(100,20)
$CompatcheckBox.Text = "Compatability"
$CompatcheckBox.Visible = $false
$form.Controls.Add($CompatcheckBox)

$ConditioncheckBox = New-Object System.Windows.Forms.CheckBox
$ConditioncheckBox.Location = New-Object System.Drawing.Point(540,280)
$ConditioncheckBox.Size = New-Object System.Drawing.Size(100,20)
$ConditioncheckBox.Text = "Condition"
$ConditioncheckBox.Visible = $false
$form.Controls.Add($ConditioncheckBox)

$FormatcheckBox = New-Object System.Windows.Forms.CheckBox
$FormatcheckBox.Location = New-Object System.Drawing.Point(550,280)
$FormatcheckBox.Size = New-Object System.Drawing.Size(100,20)
$FormatcheckBox.Text = "Format"
$FormatcheckBox.Visible = $false
$form.Controls.Add($FormatcheckBox)
#
$SerialNumbercheckBox = New-Object System.Windows.Forms.CheckBox
$SerialNumbercheckBox.Location = New-Object System.Drawing.Point(540,300)
$SerialNumbercheckBox.Size = New-Object System.Drawing.Size(100,20)
$SerialNumbercheckBox.Text = "Serial Number"
$SerialNumbercheckBox.Visible = $false
$form.Controls.Add($SerialNumbercheckBox)


#--------------------------------------------------------------
#------------Show The Window----------------------------------
$form.ShowDialog()
#-------------------------------------------------------------

