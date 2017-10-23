function Get-DhcpServerV4Information {
    [CmdletBinding()]
    param(
        [parameter(Mandatory=$true)]
        [string]        
        $ComputerName,

        [parameter(Mandatory=$true, ValueFromPipelineByPropertyName)]
        [string]
        $scopeId
    )


    Process {
        $scope = Get-DhcpServerv4Scope -ComputerName $ComputerName -ScopeId $scopeId
        #$exclusions = Get-DhcpServerv4ExclusionRange -ComputerName $ComputerName -ScopeId $scopeId
        $statistics = Get-DhcpServerv4ScopeStatistics -ComputerName $ComputerName -ScopeId $scopeId     

        $ret = [PSCustomObject]@{
            "ScopeId"=$scope.ScopeId
            "SubnetMask"=$scope.SubnetMask
            "StartRange"=$scope.StartRange
            "EndRange"=$scope.EndRange
            "Description"=$scope.Description
            "LeaseDuration"=$scope.LeaseDuration
            "Name"=$scope.Name
            "State"=$scope.State
            "PSComputerName"=$ComputerName
            "Free"=$statistics.Free
            "InUse"=$statistics.InUse
            "Reserved"=$statistics.Reserved
            "PercentageInUse"=$statistics.PercentageInUse


        }

        $ret
    }

}
