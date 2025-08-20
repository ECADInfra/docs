# Celestia Validator Incident - August 18-19, 2025

## Overview

This directory contains all documentation, analysis, and evidence related to the network-wide consensus coordination issues that affected our Celestia validator on August 18-19, 2025.

## Incident Summary

**Status**: Resolved  
**Duration**: Two separate incidents spanning August 18-19, 2025 UTC  
**Impact**: Service degradation with missed blocks due to network-wide consensus coordination issues  

### Timeline
- **First Incident**: 15:30-18:00 UTC / 08:30-11:00 PDT (August 18)
- **Second Incident**: 23:15-02:43 UTC / 16:15-19:43 PDT (August 18-19)
- **Resolution**: Both incidents resolved successfully

## Files Included

### Primary Documentation
- **[celestia-validator-incident-2025-08-18.md](celestia-validator-incident-2025-08-18.md)** - Comprehensive incident report with UTC time conversions

### Log Files (Sanitized)
- **celestia-first-incident-sanitized.log** - First incident logs (15,980 lines)
- **celestia-second-incident-sanitized.log** - Second incident logs (19,979 lines)
- **celestia-appd-last-30m-sanitized.log** - Normal operation baseline (2,786 lines)

### Analysis Files
- **celestia-errors-categorized.log** - Categorized error analysis
- **celestia-errors-summary.log** - Error summary

## Key Findings

1. **Network-Wide Issues**: Both incidents affected multiple validators simultaneously
2. **Consensus Coordination**: Issues were related to consensus timing coordination, not infrastructure failures
3. **"Timed out" vs "timeout"**: Important distinction between normal INFO messages and actual errors
4. **Duration Analysis**: Abnormally high and consistent duration values indicated underlying consensus timing issues
5. **Resolution**: First incident resolved by v5.0.2 upgrade, second by natural network recovery

## Technical Details

- **Consensus Messages**: Normal INFO level "Timed out" messages (with space)
- **Duration Pattern**: Normal operation shows variation (1000ms to 4169ms), incidents show only high values (4150-4170ms)
- **Network Impact**: Up to 47 missing validators during peak periods
- **Monitoring**: Prometheus metrics enabled early detection and data-driven responses

## Recommendations

### For Celestia Community
- Investigate distinction between "Timed out" and "timeout" messages
- Analyze whether high duration values indicate consensus timing coordination issues
- Coordinate major version updates to minimize network instability
- Implement cross-validator health monitoring

### For Our Operations
- Enhanced monitoring for consensus block time spikes
- Automated detection for network-wide consensus issues
- Community coordination for major updates

## Status

**Current Status**: No missed blocks since 02:50 UTC / 19:50 PDT on August 19, 2025  
**Resolution**: Both incidents resolved successfully with no infrastructure damage  
**Lessons Learned**: Comprehensive monitoring and data-driven responses are critical for network-wide issues
